---
layout: post
title: Alternativa a Wordpress
description: "Wordpress, Blogger... vs sistema de publicación de contenidos estáticos"
modified: 2015-01-08
tags: [Jekyll, Wordpress, Blogger, sistema de publicación de contenidos estáticos, CMS ]
image:
  feature: abstract-8.jpg
  credit: dargadgetz
  creditlink: http://www.dargadgetz.com/ios-7-abstract-wallpaper-pack-for-iphone-5-and-ipod-touch-retina/
---

 

Este post es continuación del [anterior]({% post_url 2015-12-14-Jekyll %}) y pretende explicar de una forma menos “técnica” las **diferencias entre** un sistema de gestión de contenidos o CMS dinámicos como **Wordpress** y una posible alternativa, un sistemas de publicación de contenidos estáticos como **Jekyll**.

# CMS dinámico, Wordpress

### ¿Cómo funciona?
Simplificando mucho. A partir de unas plantillas, desde una aplicación web y siguiendo unos sencillos formularios, vamos creando las diferentes páginas o post de nuestro sitio o blog. Además en Wordpress hay múltiples plugins que podemos instalar en nuestro sitio y nos dan una funcionalidad adicional a la de publicar información.


Toda esta información se guarda en la base de datos de WP y cada vez que un visitante solicita una de nuestras páginas, Wordpress genera el html que se verá en el navegador.


Aunque no lo parezca, porque como usuarios nos parece sencillo y seguramente nuestro proveedor de WP nos evite preocuparnos por estas cosas, hay una base de datos, una aplicación web que tiene que estar funcionando, versiones de esta aplicación, backups..., en el fondo una cierta complejidad asumible.


<img src="{{ site.url }}/images/20160108AlternativaWP/Wordpress.jpg" alt="Wordpress">

# La alternativa, sistema de publicación estático, Jekyll
Un sistema de publicación estático es una vuelta a los orígenes, [kiis](https://es.wikipedia.org/wiki/Principio_KISS), una vuelta a simples páginas html. Las páginas html que se muestran cuando un usuario entra en nuestro sitio web están ya construidas, no hay ningún programa que las monte según llegan las peticiones. 

### Entonces, si se trata de hacer páginas html ¿Dónde está el truco o la novedad? 

Hacer un sitio web programando html + CSS + Javascript, es largo, tedioso y puede llevarnos a errores, ya que en un sitio web muchas partes se repiten(cabeceras, pie, estilos) y el código html no es que sea muy legible.
Es en este punto donde un sistema de publicación estático nos puede servir de ayuda.

* Como todos los frameworks, nos aporta una estructura y orden que facilita el mantenimiento.
* Plantillas. Podemos definir un estilo y formato que se aplicará a todas las páginas que se generen.
* El contenido está separado del diseño. El contenido lo forman archivos de texto, sólo los textos que queremos aparezcan en nuestro sitio web y que no son comunes al resto del sitio.
* Lenguaje de marcado. Mediante una sintaxis muy sencilla podemos especificar un formato al contenido. (Títulos, negritas, enlaces)

<img src="{{ site.url }}/images/20160108AlternativaWP/Jekyll.jpg" alt="Jekyll">

# ¿Cual es la ventaja frente a un Wordpress? 

* La sencillez de llevar nuestro sitio web completo en un pendrive por ejemplo

<img src="{{ site.url }}/images/20160108AlternativaWP/PenDrive-icon.png" alt="">{: .image-right}

* Una vez creado no hace falta ningún software que no sea el navegador para tener funcionando nuestro sitio web.

<img src="{{ site.url }}/images/20160108AlternativaWP/money-icon.png" alt="">{: .image-right}

* El coste, alojar un sitio estático tiene un coste marginal hoy en día.

* La escalabilidad. Los recursos necesarios para servir un sitio estático están órdenes de magnitud por debajo de los necesarios para un CMS.
* Seguridad: No hay bugs o vulnerabilidades más allá de las del servidor de archivos. Servir contenido estático es mucho más seguro. Un CMS es una capa adicional que proteger.

<img src="{{ site.url }}/images/20160108AlternativaWP/security-Approved-icon.png" alt="">{: .image-right}

* Versiones: Una vez que el sitio estático está creado no hay problemas de versiones que actualizar. Es autocontenido.
* Backup: Tan sencillo como hacer una copia  de archivos a un disco.
* Limpieza del html generado.
* Son tantas las ventajas que incluso Wordpress tiene plugins para exportar un sitio web a contenido estático.

# ¿Y cuales son los inconvenientes?

* El más importante, en un CMS, los contenidos están disponibles tan pronto como damos a guardar. En un sistema de publicación estático es necesario compilar, crear el sitio y subirlo al servidor. Si se usa Jekyll + Github  este proceso está bastante automatizado.

* Plugins: La riqueza de plugins que tiene actualmente Wordpress para dar una funcionalidad adicional a mostrar información. Por ejemplo: formularios, tienda online… Aunque con la evolución de Javascript y componentes cada vez las páginas estáticas van a poder disponer de más funcionalidades.

<img src="{{ site.url }}/images/20160108AlternativaWP/Time-icon.png" alt="">{: .image-right}

* La curva de aprendizaje: El éxito de Wordpress es además de su difusión, la facilidad para que usuarios sin formación técnica creen sus sitios web. Crear contenido con un sistema de publicación estático requiere una formación muy por encima de la que requiere un Wordpress.

# Conclusiones:

* Los sistemas de publicación estáticos no son rival para CMS como Wordpress, pero tienen un  una oportunidad gracias a la sencillez de conceptos que los sustenta, y más especialmente con el auge de Javascript + APIs REST.
* Un equipo podría diseñar plantillas para Jekyll, de la misma manera que se diseñan para Wordpress, crear  un sistema de publicación como tiene Github (ver post anterior) y así poder crear contenido estático de mucha calidad y sobre todo muy barato de mantener.  
* Entre otras cosas a mi me sirve para crear y publicar este blog.  ;-)



