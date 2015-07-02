layout: post
title: PHP no es el Santo Grial del Desarrollo Web
alias: 2011/08/24/php-no-es-el-santo-grial-del-desarrollo-web/
permalink: php-no-es-el-santo-grial-del-desarrollo-web
date: 2011-08-24
categories: 
- Opinion 
- PHP
---
_Post originalmente publicado en [Zonaphp.com](http://www.zonaphp.com) pero movido a RuidoDigital ya que se trata de una opinión más personal._

Me encontraba leyendo mis feeds el día de hoy cuando me cruzo con el post [PHP, ¿Por qué es el más usado?](http://www.elwebmaster.com/general/php-por-que-mas-usado) dentro de ElWebmaster.com, un post traducido (no enteramente) del post original [WHY IS PHP SO HEAVILY USED BY TODAY’S DEVELOPERS?](http://desizntech.info/2011/07/why-is-php-so-heavily-used-by-today%E2%80%99s-developers/). Y no puedo más que estar en desacuerdo con los ejemplos dados.

Está bien que queramos mucho a PHP, nos da de comer y nos permite **crear sitios web dinámicos con relativa facilidad**, pero de ahi a achacarle ventajas que no tiene, es algo que me parece que desinforma más que ayudar a adoptar esta tecnología.
<!--more-->

El ejemplo que dan de Facebook convirtiendo su plataforma de PHP a C++ es el **ejemplo fundamental que PHP no es un lenguaje preparado para grandes cantidades de tráfico**, dado que tuvo que convertirse una plataforma hacia C++, un lenguaje tipado, no-dinamico, para poder soportar la cantidad de visitas. De hecho, Facebook hoy por hoy podría programarse en cualquier lenguaje de alto nivel, siempre que haya un traductor hacia C++.

PHP no es un lenguaje eficiente, y lo sabe cualquier persona que utilice PHP 3 o 4 años. Lo queremos mucho, es el lenguaje que nos permite hacer muchas cosas en Internet, pero **cada petición, al crear todo el ambiente de cero**, consume 15 megas de memoria mínimo por request. Esto significa que en un servidor con 8 Gigas de memoria, no se podrían servir más de 500 usuarios concurrentes, antes que el servidor deje de responder (probablemente prendido fuego).

Que den como ejemplo de Flexibilidad que PHP pueda trabajar con XML y HTML es casi tonto. Yo entiendo que tengan que cargar artículos seguido para el blog, y para eso traduzcan los contenidos lo más rápidamente posible, pero incluso el autor original falla en este punto. No es cierto que un PHP funcione automáticamente en cualquier plataforma, ya que algo programado en Windows puede muy bien no funcionar en Mac, **dada la diferencia de arquitecturas del procesador**.

Entonces, PHP cubre un amplio aspecto del desarrollo actual, y permanece aún con altos porcentajes de uso porque hay mucho desarrollador que no ha estudiado otras plataformas, y porque hay un gran parque de aplicaciones ya desarrolladas, pero no es por las características que dan en el post mencionado. Hoy por hoy ya muchos han migrado a **Ruby** (o RoR) o **Python**, para la creación de aplicaciones web eficientes. Incluso se está escuchando pisar fuerte a [Node.js](http://nodejs.org/) en el lado del servidor.
