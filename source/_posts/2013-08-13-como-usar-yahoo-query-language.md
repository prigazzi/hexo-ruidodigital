layout: post
title: "Cómo usar Yahoo Query Language"
permalink: como-user-yahoo-query-language
date: 2013-08-13
categories: [Javascript, APIs]
---
Con la mudanza del blog, uno de los primeros temas a los que quería dedicarme era generar una buena página de Error 404 donde aquellas personas que llegaran desde links desactualizados, pudieran tener acceso al viejo contenido de manera sencilla. Les dejo [un ejemplo de lo que buscaba lograr](http://www.ruidodigital.com/2011/08/31/ajustar-el-tamano-de-imagenes-facilmente-en-ubuntu/). Comencé creando un archivo **404.html** en la raíz del blog y agregué una línea a mi .htaccess (si, estoy hospedando con Apache en este momento).

``` apache .htaccess
ErrorDocument 404 /404.html
```

Ahora viene lo interesante. Dado que estoy utilizando [Jekyll como generador del blog]({% post_url 2013-03-03-comenzando-un-blog-de-cero %}), no tengo soporte de un lenguaje del lado del servidor. **Son todos archivos estáticos**. Mi solución tendría que venir del lado del cliente, así que pensé : _¿De qué manera puedo chequear la existencia de un sitio web, desde Javascript?_ <!--more-->

Aquí es donde [Yahoo Query Language](http://developer.yahoo.com/yql/) viene al rescate. Yahoo Query Language (a partir de ahora **YQL**) es una serie de datos estructurados puestos a disposición del público por parte de Yahoo. Los podemos consultar haciendo uso de una API, desde diferentes tipos de lenguajes de programación, y recibiendo los datos ya sea en XML o en formato JSON. Incluso, tenemos una [consola para realizar pruebas](http://developer.yahoo.com/yql/console/).

### Cómo obtener información de sitios web

Volviendo al ejemplo de la página de Error 404, lo que necesitaba era chequear la existencia de la url que se había accedido, pero cambiando el subdominio _www_ por _old_. Esto es sencillo gracias a `document.URL` y un poco de expresiones regulares:

``` js
var old_url = document.URL.replace(/((www\.)?ruidodigital)/gm, "old.ruidodigital");
```

Teniendo la url que queremos chequear dentro de `old_url`, armamos el Query que vamos a ejecutar contra YQL. Lo que queremos es obtener el `title` de la url, si es que esta existe, entonces, el query que vamos a ejecutar se vería así:

``` sql
SELECT * FROM html
WHERE url = "{old_url_aqui}"
AND xpath='//title'
```

Para ejecutar este query, lo que debemos hacer es armar una URL completa haciendo la llamada a YQL. El primer (y único) problema que nos encontramos, es que al estar en un dominio distinto al del blog, no podemos hacer una llamada Ajax y listo, tenemos que saltarnos esa limitación. Por suerte, YQL nos ofrece la manera de declarar un método **callback** en la petición, que envolverá a nuestros datos recibidos, y ejecutará una llamada a dicho método si estuviera definido en nuestro código. Es más sencillo verlo implementado.

``` js
var to_old = url.replace(/((www\.)?ruidodigital)/gm, "old.ruidodigital");
var query = "http://query.yahooapis.com/v1/public/yql?"+
			"q=SELECT%20*%20from%20html%20WHERE%20url%3D%22"+encodeURIComponent(to_old)+
			"%22%20and%0A%20xpath%3D%27%2F%2Ftitle%27&format=json&callback=show_result";

$(function()
{
	var head = document.getElementsByTagName('head')[0];
	var js = document.createElement("script");
	js.type="text/javascript"; js.src = query;
	head.appendChild(js);
})

```

De esta manera, al ejecutar esta parte del código, lo que recibiremos dentro del tag `script` que acabamos de crear y anexar al head, es una respuesta en JSON como la siguiente (usando como ejemplo, la url **http://old.ruidodigital.com**): 

``` json
show_result({
    "query": {
        "count": 1,
        "created": "2013-08-14T13:18:11Z",
        "lang": "en-US",
        "results": {
            "title": "RuidoDigital"
        }
    }
});
```

Solo nos queda definir en alguna parte de nuestro código, un método llamado `show_results` que haga algo útil con la información recibida y completamos de esa manera la página de Error 404 que le _sugiere_ a los visitantes, acceder al contenido viejo del blog.

``` html
<p id="sugerencia" class="well well-small" style="display: none;">
	Parece que ingresaste buscando <span id="url" style="font-weight: bold;"></span>, que ya no se encuentra disponible en este blog, pero aún puedes leerlo en el viejo <span class="logo">ruido<span>digital</span></span>: <a id="oldurl" href=""></a>.
</p>
<script>
	function show_result(rs)
	{
		if(rs.query.count) {
			$('#sugerencia #url').html(url);
			$('#sugerencia #oldurl')
				.attr('href', to_old)
				.html(rs.query.results.title);
			$('#sugerencia').slideDown();
		}
	}
</script>
```

¿Qué opinan de la implementación utilizando YQL? ¿Qué cambios le realizarían al código o al concepto de la página de Error 404?

