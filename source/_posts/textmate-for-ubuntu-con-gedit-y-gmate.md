layout: post
title: Textmate for Ubuntu con Gedit y Gmate
alias: 2011/09/27/textmate-for-ubuntu-con-gedit-y-gmate/
permalink: textmate-for-ubuntu-con-gedit-y-gmate
date: 2011-09-27
categories: 
- Desarrollo 
---
Si da la maravillosa casualidad que están **desarrollando para la web**, utilizando este Sistema Operativo gratuito conocido como [Ubuntu](http://www.ubuntu.com), entonces lo más seguro es que se hayan cruzado, en algún momento, con su editor de texto [Gedit](http://projects.gnome.org/gedit/). Algo escueto y **sin muchas características**, cumple su propósito con un esquema de color configurable, espacios configurables y automáticos, números de linea y no mucho más.

Pero todo esto cambia de la mano de **[Gmate](https://github.com/gmate/gmate)**, un grupo de plugins para Gedit, orientados a ofrecer una experiencia de usuario similar a la que ofrece [Textmate](http://macromates.com/) en MacOs (una excelente opción para el Sistema Operativo de la manzanita, pero que tiene **un precio de 56 dólares**).
<!--more-->

Instalarlo es muy simple. En una consola tipeamos:

    sudo apt-add-repository ppa:ubuntu-on-rails/ppa
    sudo apt-get update
    sudo apt-get install gedit-gmate

Algunos de los plugins incorporados son:

* **Classbrowser**. Un navegador de clases basado en [c-tags](http://ctags.sourceforge.net/).

* **Fuzzy Open**. Método rápido para abrir archivos con Shift+Ctrl+O.

* **Gedit Open File**. Similar al anterior, solo que soporta expresiones regulares igual que Textmate

* **Find in Project**. Búsqueda dentro de un proyecto, en varios archivos al mismo tiempo.

* **Gedit Todo.** Muestras las marcas TODO, IMPROVE, FIXME, etc, dentro del código del proyecto.

* **Gemini.** Autocompleción de pares de caracteres [{'""'}]

* **Quickhighligthmode.** Cambia rápidamente el método de coloreo de código.

* **Regex Search Replace**. Buscar y reemplazar utilizando expresiones 

regulares.
* **Text Tools.** Algunas mejoras en el manejo de lineas de texto: subir, eliminar, duplicar, etc.

* **Trailsave**. Elimina el espacio al final del archivo al momento de guardar.

* **Word Completion.** Ofrece autocompletado de palabras utilizadas dentro del documento.

* **Multi Edit.** Permite escribir al mismo tiempo en distintas partes del archivo.

* **Zen Coding.** Fantástica herramienta para escribir menos a la hora de crear HTML y CSS.

