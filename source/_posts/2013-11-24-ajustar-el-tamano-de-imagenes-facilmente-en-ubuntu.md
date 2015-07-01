layout: post
title: Ajustar el tamaño de imágenes fácilmente en Ubuntu
date: 2011-08-31
alias: 2011/08/31/ajustar-el-tamano-de-imagenes-facilmente-en-ubuntu
permalink: ajustar-el-tamano-de-imagenes-facilmente-en-ubuntu
categories:
- General
---
Si bien hace un tiempo que en Ubuntu es relativamente sencillo rotar una imagen, gracias al **visualizador por defecto de imágenes** [(Eye of Gnome)](http://www.hola.com), sigue siendo bastante engorroso tener que abrir el Gimp solo para cambiar el tamaño de una imagen. Una tarea que, en el día a día promedio de cualquier desarrollador, es bastante recurrente.

¿Habría algo más sencillo? Pero claro que si! Buscando en Synaptics encontré justo lo que necesitaba: **Nautilus Image Converter**. Ejecutando los siguientes comandos en una Terminal (para abrir la Terminal, `Ctrl+Alt+T):

    sudo apt-get install nautilus-image-converter
    nautilus -q; nautilus &

Ya lo tenemos instalado y listo para utilizar. Ahora simplemente y desde nuestro administrador de archivos, podemos hacer click derecho y cambiar el tamaño de cualquier imagen.

![Ejemplo al hacer click derecho](/images/Screenshot2.png)