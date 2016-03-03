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

# Avance 1 

by  [Sebastian Chaves](https://github.com/adamantwharf) - [Laura Santos](https://github.com/lsfinite) - [Jimmy Pulido](https://github.com/jiapulidoar)

H:

# Index

<!-- .slide: data-background="#7E2121" --> 

 1. Introducción <!-- .element: class="fragment" data-fragment-index="1"-->
 1. Descripción del Problema <!-- .element: class="fragment" data-fragment-index="2"-->
 1. Diagrama E/R <!-- .element: class="fragment" data-fragment-index="3"-->
 
	
H:

# Introducción 
<!-- .slide: data-background="#005050" -->
V:
 
 ## Necesidad de una Base de datos

 Spa como eleccion de la entidad. <!-- .element: class="fragment" data-fragment-index="1"-->

 Habrá un acceso completo a la información (funcionamiento interno). <!-- .element: class="fragment" data-fragment-index="2"-->

 Existe interés de implementación completa por parte de la entidad. <!-- .element: class="fragment" data-fragment-index="3"--> 

V:
## Objetivo principal 


  >Facilitar y mejorar el manejo interno de la información del Spa.  

  Actualmente lo implementan por medio de una hoja de Cálculo. 



H:
# Descripción del Problema
<!-- .slide: data-background="#7E2121"  -->
V:

## Problema 

Diseñar una base de datos útil para un centro de estética. 

Se pretende crear: 

> Resgistro para consulta y análisis de datos que contribuirá a la toma de desiciones financieras. 


V:

##Contribuyendo a:

* Facilitar actualizaciones (Clientes, proveedores, trabajadores, etc). 

* Evitar la repetición de información. 
 
* Ahorro de recursos humanos. 

* Mitigar el trabajo inneceario (Forma manual). 

* Reducir el error. 

V:

## Detalles específicos: 

El centro de estérica consta de dos secciones: 
Productos y servicios

> 
  * Venta de Productos
  * Venta de Servicios 

Ambos con atributos específicos y comunes.

V:

##Entidades a identificar 

* Producto y servicio. 
* Cliente.
* Proveedor. 
* Empleado. 
* Protocolo (Procedimiento a seguir). 


>Se dispuso de un completo análisis para identificar sus relaciones, generando más entidades de las presentadas.

H: 
<!-- .slide: data-background="#005050" -->
##Diagrama entidad Relación

 
 <iframe src="diagrama.pdf" style="width:750px; height:1000px;" frameborder="0"></iframe>
