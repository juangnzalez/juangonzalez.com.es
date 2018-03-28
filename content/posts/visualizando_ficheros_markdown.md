---
title: "Visualizando ficheros markdown"
date: 2017-10-04T18:55:17+02:00
draft: true
---

El lenguaje de marcado [Markdown](https://es.wikipedia.org/wiki/Markdown) está diseñado para tener buena legibilidad del fichero origen, pero con poco trabajo podemos __interpretar el fichero y mostrar en consola el resultado mejorando aún más la legibilidad del documento__.

## Opciones

Una puede ser _interpretar_ el fichero de texto con formato _markdown_ con el conversor de ficheros [Pandoc](https://pandoc.org/) y pasar la salida a un navegador tipo [Lynx](http://lynx.browser.org/) o [w3m](http://w3m.sourceforge.net/).

En una línea sería algo como:

``` shell
pandoc -t html ejemplo.md | lynx -stdin

pandoc -t html ejemplo.md | w3m -T text/html
```

Y otra es utilizar una __aplicación específica__ para este fin como pueden ser 
[mdr](https://github.com/mrchimp/mdr "Markdown reader with color"), [mdless](http://brettterpstra.com/projects/mdless/ "More Markdown, Less less") (del gran [Brett Terpstra](http://brettterpstra.com/)) o [mdv](https://github.com/axiros/terminal_markdown_viewer "Styled Terminal Markdown Viewer").

* [mdr](https://github.com/mrchimp/mdr "Markdown reader with color") es interesante para visualizar ficheros _markdown_ de un repositorio [GitHub](https://github.com/). Por ejemplo `mdr -g mrchimp/mdr` nos mostrará el `README.md` del repositorio `mdr` que el usuario `mrchip` tiene en [GitHub](https://github.com/).
* [mdless](http://brettterpstra.com/projects/mdless/ "More Markdown, Less less") tiene por principal característica que es un _paginador_ y las opciones de visualización.
* [mdv](https://github.com/axiros/terminal_markdown_viewer "Styled Terminal Markdown Viewer") es el que más utilizo. En el siguiente apartado tenemos una breve descripción de esta aplicación.

## mdv

[mdv](https://github.com/axiros/terminal_markdown_viewer "Styled Terminal Markdown Viewer") es, según su autor, un visor de ficheros _markdown_ basado en _Python_ y desarrollado con la idea de facilitar el trabajo con ficheros _markdown_ sin obligar a un cambio de contexto de _terminal_ en la creación al _navegador_ en la visualización.

El visor utiliza colores, formateo de tablas y resaltado de código para mejorar la lectura del documento.

Tenemos a nuestra disposición multitud de temas registrados en el `ansi_tables.json` localizado en:

``` shell
pip show mdv | grep Location 
```

En este fichero podemos añadir o editar un tema existente. Este es el que utilizo yo:

```
   "000.1331": {
        "name": "juangonzalez", 
        "ct": [
            "191", 
            "69", 
            "205", 
            "207", 
            "63"
        ]
    }
```

Podemos ajustar los colores que se utilizarán para cada elemento del documento editando el `markdownviewer.py` tal y como se describe en la ayuda de la aplicación. Mi configuración actual es:

```
# ansi cols (default):
# R: Red (warnings), L: low visi, BG: background, BGL: background light, C=code
# H1 - H5 = the theme, the numbers are the ansi color codes:
H1, H2, H3, H4, H5, R, L, BG, BGL, T, TL, C = \
    231, 153, 64, 109, 165, 124, 24, 16, 188, 255, 59, 208
# Code (C is fallback if we have no lexer). Default: Same theme:
CH1, CH2, CH3, CH4, CH5 = H1, H2, H3, H4, H5

```

La instalación se hará con un:

```
pip install mdv
```

Arrancamos con:

```
mdv ejemplo.md
```

Si lanzamos la aplicación con un `mdv -h` obtendremos un listado de las opciones disponibles. Si lo lanzamos sin parámetros, se mostrará cómo se interpreta un pequeño ejemplo.

Además implementa un monitor de cambios en el fichero con lo que podemos _simular_ un sistema de pre visualización _instantánea_ mientras editamos nuestro fichero.

Para terminar un gif como resumen del _post_.

[![asciicast](https://asciinema.org/a/HbE4atNl6IuLOGIwMdVIBjtiQ.png)](https://asciinema.org/a/HbE4atNl6IuLOGIwMdVIBjtiQ)



