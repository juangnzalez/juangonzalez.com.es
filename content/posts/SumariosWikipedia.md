---
title: "Obteniendo resúmenes de la Wikipedia desde CLI"
date: 2018-02-11T18:40:18+01:00
draft: true
---

>A diario consultamos la [Wikipedia](https://www.wikipedia.org/). En muchas ocasiones no necesitamos leemos el artículo entero, nos basta con las primeras líneas para resolver la duda que tenemos.

En este post presentaré dos aplicaciones muy útiles para realizar estas consultas rápidas a la [Wikipedia](https://www.wikipedia.org/). Las dos son muy parecidas, difieren en los requisitos y poco más.

Observaréis que los _resúmenes_ que nos devuelven las aplicaciones son las líneas que van desde el título hasta el inicio de la *Tabla de Contenidos* del artículo que se ajuste a nuestra consulta.

## Consultas rápidas en la Wikipedia: WIKI

La primera de las dos aplicaciones que comentaba en la introducción es **WIKI** que según podemos leer en [walle/wiki: Command line tool to fetch summaries from MediaWiki wikis, like Wikipedia](https://github.com/walle/wiki) es una aplicación para obtener resúmenes de la Wikipedia desde la línea de comandos. Además puede obtener resúmenes de cualquier **wiki** creado con el software de [MediaWiki](https://www.mediawiki.org/wiki/MediaWiki/es) y que tenga la [API](https://www.mediawiki.org/wiki/API:Main_page/es) activa. Esta es para mí una de las características más reseñables de esta aplicación y que puede hacer que la elijamos frente a la siguiente.

### Instalación

En primer lugar necesitamos tener instalado [The Go Programming Language](https://golang.org/) en nuestro equipo e incluir en nuestro `PATH` el directorio `$GOPATH/bin` ([How to Write Go Code - The Go Programming Language](https://golang.org/doc/code.html#GOPATH))


A continuación con un `go get github.com/walle/wiki/cmd/wiki` tendremos la aplicación lista para usar.

### Uso

Un inicio puede ser lanzar un `wiki -h`

Según la ayuda con `wiki -l es CONSULTA` obtendremos resultados para nuestra consulta desde [Wikipedia, la enciclopedia libre](https://es.wikipedia.org/wiki/Wikipedia:Portada)

En la presentación de esta aplicación comentaba que la posibilidad de consultar con ella otras wikis además de la Wikipedia era una característica que para mí podía resultar determinante a la hora de elegirla frente a otras pero me temo que no he conseguido que funcione. 
El ejemplo que proponen en la web del repositorio de la aplicación `wiki -u https://en.wikiversity.org/w/api.php physics` sí que devuelve un resultado pero en los intentos que he hecho para lanzar consultas sobre [Wikcionario](https://es.wiktionary.org/wiki/Wikcionario:Portada) o sobre [ArchWiki](https://wiki.archlinux.org/) nunca he conseguido resultados. Por ejemplo un `wiki -u https://es.wiktionary.org/w/api.php tortuga` devuelve 

```
No such page
Create it on: https://es.wiktionary.org/wiki/tortuga
```

Lo cual no es cierto. Esta [URL](https://es.wiktionary.org/wiki/tortuga) sí que existe.

Intentaré ponerme en contacto con el autor en GitHub y le consultaré este punto. Si tengo noticias al respecto actualizaré el post.

## WIKIT. Obtener resúmenes de la Wikipedia de forma fácil.

La segunda aplicación es **WIKIT** [KorySchneider/wikit: Wikipedia summaries from the command line](https://github.com/KorySchneider/wikit) que al igual que la anterior nos lanzará una consulta sobre la Wikipedia y nos devolverá las líneas comprendidas ente el título y la *Tabla de Contenidos*.

### Instalación

El requisito previo es tener instalado en nuestro sistema el gestor de paquetes [npm](https://www.npmjs.com/).

Con un `npm install wikit -g` tendremos la aplicación lista para usar en nuestro sistema.

### Uso

Lanzamos la aplicación con un `wikit <consulta> [-opciones]`. 

Para consulta [Wikipedia, la enciclopedia libre](https://es.wikipedia.org/wiki/Wikipedia:Portada) utilizaremos la opción `-l es`, por ejemplo `wikit línea de comandos -l es`

Con la opción `-b` abriremos el artículo completo resultado de la búsqueda en Wikipedia en el navegador que tengamos definido por defecto en nuestro sistema.

Es posible que nuestra búsqueda devuelva más de un artículo. En este caso la aplicación abrirá la página de la Wikipedia con los posibles resultados en nuestro navegador por defecto.

## Conclusión.

Para la consulta básica y rápida en Wikipedia cualquiera de las dos aplicaciones funciona muy bien. La ejecución de ambas tiene pocas opciones; personalmente no creo que se necesiten más aunque sí que sería deseable que funcionaran todas las que ofrecen. En cualquier caso creo que son dos aplicaciones muy útiles.

Un pequeño resumen para terminar:

[![asciicast](https://asciinema.org/a/viSUlqiQEwkS0yweEjpfglIOw.png)](https://asciinema.org/a/viSUlqiQEwkS0yweEjpfglIOw)
