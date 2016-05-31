<section id="themes">
	<h2>Themes</h2>
		<p>
			Set your presentation theme: <br>
			<!-- Hacks to swap themes after the page has loaded. Not flexible and only intended for the reveal.js demo deck. -->
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/black.css'); return false;">Black (default)</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/white.css'); return false;">White</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/league.css'); return false;">League</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/sky.css'); return false;">Sky</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/beige.css'); return false;">Beige</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/simple.css'); return false;">Simple</a> <br>
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/serif.css'); return false;">Serif</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/night.css'); return false;">Night</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/moon.css'); return false;">Moon</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/solarized.css'); return false;">Solarized</a>
		</p>
</section>

H:

# Entrega final 
<!-- .slide: data-background="#ffffff" --> 
by  [Sebastian Chaves](https://github.com/adamantwharf) - [Laura Santos](https://github.com/lsfinite) - [Jimmy Pulido](https://github.com/jiapulidoar)
### Link presentación 
>http://futureun.github.io/BDPresentacion/

H:

# Index

<!-- .slide: data-background="#7E2121" --> 

 1. Centro de Estética <!-- .element: class="fragment" data-fragment-index="1"-->
 1. Usuarios y permisos  <!-- .element: class="fragment" data-fragment-index="2"-->
 1. Vistas, Pa, Triggers  <!-- .element: class="fragment" data-fragment-index="3"-->
 2. transacciones, cursores <!-- .element: class="fragment" data-fragment-index="4"-->
	
H:

# Centro de EStética
<!-- .slide: data-background="#005050" -->

Base de datos para un centro de estética <!-- .element: class="fragment" data-fragment-index="1"-->


H: 
<!-- .slide: data-background="#005050" -->
##Diagrama entidad Relación

 
 <iframe src="diagrama.pdf" style="width:750px; height:600px;" frameborder="0"></iframe>

H:
<!-- .slide: data-background="#005050" -->
##Diccionario
 <iframe src="diccionario.pdf" style="width:750px; height:600px;" frameborder="0"></iframe>

H:
# Usuarios y permisos 
<!-- .slide: data-background="#7E2121"  -->
Siguiendo las necesidades del centro de estética, consideramos oportuno dividir a los usuarios en las siguientes clasificaciones:
V:

## Empleados: 
>Los empleados, se dividirán en cuatro rangos de acceso según su cargo dentro del centro de estética:

* Peluqueros y esteticistas
* Recepcionistas 
* Gerente 
* Mantenimiento


V:
## Peluqueros y esteticistas

Tendrán acceso a:

* Modificar datos personales
* Consultas: Agenda de citas y Horario de trabajo.

>En el caso de Agendar citas tnedrá que consultar con el cliente y además deberá contar con un permiso dado por el recepcionista. 

V:
## Recepcionistas
>Son los encargados de atender directamente al cliente y manejar la caja, tendrán acceso a: 

* Su información
* Acceso completo a la agenda de citas
* Inventarios de los productos (venta y gasto de un producto).

V:
## Gerente 
>Encargado de Administrar la estética en general, el acceso a la base de datos será de tipo administrador.

* Será quien registre las transacciones con los proveedores y la parte contable. 
* Manejará los horarios de los empleados. 

V:
##Mantenimiento 
>Encargados de los servicios de limpieza y mantenimineto, solo tendrán acceso para modificar y consultar sus datos personales. 

V:

##Clientes

>Los clientes tendrán las posibilidad de:

*Modificar sus datos personales
*Cancelar citas programadas. 
*Sus consultas pueden ser:
	horario de trabajo de los empleados y su propia agenda de citas. 

H:
## Vistas, PA, Triggers

V:
## Tabla Permisos

 <iframe src="permisos.pdf" style="width:750px; height:600px;" frameborder="0"></iframe>
 
V: 
## Tabla Vistas, Triggers y PA

 <iframe src="triggers.pdf" style="width:750px; height:600px;" frameborder="0"></iframe>

V: 
## Triggers 
Ejemplo:  Trigger que determina el valor acumulado de una compra al proveedor 
```java
<!-- 
DELIMITER $$
  CREATE TRIGGER trig_adquis before INSERT ON Adquisicion
    FOR EACH ROW BEGIN
    
      declare sum_total int default 0;
      declare sum_parcial int default 0;
      set sum_parcial = (select CPRO_costo from CompraProveedor where 
      CompraProveedor.idCompraProveedor = new.CompraProveedor_idCompraProveedor);
      set sum_total = sum_parcial + new.adq_preciocompra;
      update CompraProveedor set CPRO_costo = sum_total where 
      CompraProveedor.idCompraProveedor = new.CompraProveedor_idCompraProveedor;
     END$$
DELIMITER ;
-->
```
V: 
## Vistas 
Ejemplo: Muestra la lista de ventas detalladas realizadas por los empleados 
```java
<!-- 
Create view ventas_realizadas as select ven_id, ven_fecha, Ven_costo,cli_cc, concat(cli_nombre,' ',cli_apellido) 
from Venta join Empleado on Ven_Emp_cc = Emp_cc join Cliente using (Cli_cc) where Emp_cc = (select user from mysql.user where user()=concat(mysql.user.user,"@",mysql.user.host)) ;
-->
```
V:
## Procedimientos almacenados 
Ejemplo: Procedimiento que determina, dado un producto, la cantidad total 
```java
<!-- 
DELIMITER $$
 CREATE PROCEDURE disponibilidad_produ(produ INT)
   BEGIN
     declare cantidad int default 0;
     set cantidad = (select count(idAdquisicion) from producto join adquisicion on (Producto_Pro_id = Pro_id) 
     join inventario on ( Adquisicion_idAdquisicion = idAdquisicion) where Pro_id = produ and disponible = 1);
     select cantidad;
   END $$
DELIMITER ;
-->
```
H: 
## Transacciones
Ejemplo: Verifica la legitimidad de la compra proveedor
```java
<!-- 
DELIMITER $$ 
  create procedure proc_transaccion_compraProv(id int, produ_id int , id_compraProv int , adq_precio int , fecha_ven date)
  begin
	declare estado_i double;
	start transaction ;
    set estado_i = ( select Tran_estado_final from Transaccion order by idTransaccion desc limit 1 );
    INSERT INTO `estetica`.`Adquisicion` (`idAdquisicion`, `Producto_Pro_id`, `CompraProveedor_idCompraProveedor`, `adq_preciocompra`, `Fecha_Vencimiento`)
    VALUES (id, produ_id, id_compraProv, adq_precio, fecha_ven);
    if (adq_precio > estado_i) then
		rollback;
    else 
		commit;
    end if;    
		
  end$$
delimiter ;
-->
```
V: 
##Cursores 
Ejemplo:  Determina los productos vencidos tomando como referencia la fecha actual, me muestra los resultados 
```java
<!--
DELIMITER $$
CREATE PROCEDURE det_vencimiento()
	BEGIN
	declare done INT DEFAULT 0;
    declare fecha_ven date ;
    declare id int default 0;
	DECLARE det_venci cursor
		for select fecha_vencimiento, idAdquisicion from Adquisicion;
	Declare continue handler for sqlstate '02000' set done = 1;
    open det_venci;
	REPEAT
	fetch det_venci into fecha_ven, id ;
	if not done then
		if fecha_ven < curdate() then 
        update inventario set inventario.disponible = 0, inventario.estado = 'rojo' where
         inventario.Adquisicion_idAdquisicion = id; 
        end if;
	end if;
	until done END REPEAT;
    select idInventario, Pro_nombre,adq_preciocompra, fecha_vencimiento from inventario join Adquisicion 
    on ( Adquisicion_idAdquisicion = idAdquisicion) join Producto on (Producto_Pro_id= Pro_id) where estado like '%rojo%'; 
	close det_venci; END$$ 
DELIMITER ;
-->
```

