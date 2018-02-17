---
title: "Manejando iTunes desde la Línea de Comandos"
date: 2018-02-16T17:33:07+01:00
draft: true
---

>iTunes es la aplicación que utilizo para manejar mi biblioteca de música. En este post hablaré sobre dos aplicaciones que uso para controlar _iTunes_ desde la _Línea de Comandos_.

He de comenzar diciendo que no he encontrado una aplicación que tenga todas las opciones que necesito pero con las dos que os presento en este post consigo resolver bastante bien la tarea.

## `iTunes-remote` buscando en nuestra biblioteca.

[mischah/itunes-remote: Control iTunes via CLI](https://github.com/mischah/itunes-remote)

Esta aplicación es la más completa que he encontrado para interactuar con la biblioteca de *iTunes*.

### Instalación

Requiere del gestor de paquetes [npm](https://www.npmjs.com/)

Una vez cubierto este requerimiento solo tenemos que hacer un 

```
npm install itunes-remote -g
```

para tener la aplicación instalada en nuestro sistema.

### Uso

Lanzamos la aplicación con un `itunes`. Se nos abre un _prompt_ tal que `iTunes:` y podemos empezar a utilizar la aplicación.

El primer comando que le pasamos es un `help` con lo que se nos muestran todas las opciones disponibles.

Para mí las dos más interesantes de esta aplicación son la de `play {artist,album}` y la de `search`.

#### Opción `search`

Con `search -A <disco>` realizamos una búsqueda en nuestra biblioteca del album  `<disco>`. Con `search -a <artista>` la búsqueda será por artista. Con los resultados de la búsqueda se creará una lista de reproducción llamada _itunes-remote_ y se iniciará la reproducción de la primera canción de la lista.

#### Opción `play`

En lugar de la búsqueda previa podemos empezar la reproducción de música con una lista de canciones de un artista o grupo determinado. Para ello contamos con el comando `play {artist,album}`.

Un `play artist` nos creará una lista de los artistas/grupos que tengamos en nuestra biblioteca y nos pedirá que seleccionemos uno. Con nuestra elección creará una lista de reproducción con todas las canciones que tengamos en *iTunes* para el artista/grupo seleccionado.

El comando `play album` es similar. Se genera una lista con los discos de nuestra colección, seleccionamos uno y comienza la reproducción de la lista de reproducción que se genera.

Además de estos dos comandos disponemos de los `play`, `stop`, `pause`, `next`, `previous` y `stop` esperados pero no tenemos ninguno para controlar el volumen o mostrar e título de la pista que se está reproduciendo en ese momento. Para resolver esta carencia tenemos la aplicación que comento a continuación.

## `m-cli` la _navaja suiza_ para macOS 

[rgcr/m-cli:  Swiss Army Knife for macOS](https://github.com/rgcr/m-cli) es un paquete que reune un buen número de pequeñas utilidades para macOS ejecutables desde la línea de comandos.

### Instalación

Con un `brew install m-cli` tendremos el paquete instalado en nuestro sistema. Dudo que no tengas **Homebrew** instalado, pero por si acaso  ... [Homebrew — El gestor de paquetes para macOS que faltaba](https://brew.sh/index_es.html).

### Uso

Es imprescindible consultar la ayuda de este paquete (`m help`). Disponemos de muchos comandos u opciones muy interesantes pero las que nos interesan en este post son la de `volume` y la obvia `itunes`.

#### Opción `volume`

Si lanzamos un `m volume` desde el prompt de nuestra shell obtendremos el estado actual del volumen de la salida activa de sonido en nuestro sistema en una escala de 0 a 100.

Con `volume <n>` siendo `<n>` un número entre 0 y 100, fijaremos el volumen del sonido.

#### Opción `itunes`

Con `m itunes help` obtendremos un listado de los parámetros que le podemos pasar a esta opción. 

Disponemos de `play`, `stop`, `next`, `prev`, `pause`. Todas estas son acciones que puedo lanzar desde las teclas _multimedia_ del teclado o desde los controles del altavoz bluetooh que vengo utilizando con los que nos las suelo usar.

Los parámetros que me son útiles del comando `m itunes` son:

 - `status` que nos muestra el artista/título de la canción que se está reproducciendo en ese momento.

 - `itunes col {op,down,#}` con la que controlamos el volumen. Tenemos dividido el volumen en una escala de 0 a 100 como ya comentaba en la descripción de la opción `volume`. Con `vol up` incrementamos el nivel actual en _5_ unidades, con `vol down` redusimos el volumen en _5_ unidades. Por último `m itunes vol #` es equivalente al ya descrito `m volume`. 

## Conclusión.

 A falta de la aplicación _definitiva_ para línea de comandos que nos permita controlar la reproducción de música almacenada en nuestra biblioteca _iTunes_ creo que con estas dos aplicaciones resolvemos bastante bien la tarea.

 Como siempre, un pequeño gif resumen de los comentado en el post.

[![asciicast](https://asciinema.org/a/xReWVaPt4MkQv90AyEEHgv50K.png)](https://asciinema.org/a/xReWVaPt4MkQv90AyEEHgv50K)
