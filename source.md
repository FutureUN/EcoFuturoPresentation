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

# Avance 2 

by  [Sebastian Chaves](https://github.com/adamantwharf) - [Laura Santos](https://github.com/lsfinite) - [Jimmy Pulido](https://github.com/jiapulidoar)

H:
<!-- .slide: data-background="#ffffff" --> 
# Link presentación 
>http://futureun.github.io/BDPresentacion/

H:

# Index

<!-- .slide: data-background="#7E2121" --> 

 1. Centro de Estética <!-- .element: class="fragment" data-fragment-index="1"-->
 1. Usuarios y Perfiles de la base de datos <!-- .element: class="fragment" data-fragment-index="2"-->
 1. Consultas <!-- .element: class="fragment" data-fragment-index="3"-->
 
	
H:

# Centro de EStética
<!-- .slide: data-background="#005050" -->

Base de datos para un centro de estética <!-- .element: class="fragment" data-fragment-index="1"-->



H:
# Usuarios y Perfiles
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


```
H: 
<!-- .slide: data-background="#005050" -->
##Diagrama entidad Relación

 
 <iframe src="diagrama.pdf" style="width:750px; height:600px;" frameborder="0"></iframe>

H:
<!-- .slide: data-background="#005050" -->
##Diccionario
 <iframe src="diccionario.pdf" style="width:750px; height:600px;" frameborder="0"></iframe>
```
