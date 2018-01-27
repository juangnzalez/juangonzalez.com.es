---
title: "Usando less +F como sustituto de tail -f" 
date: 2017-09-18T16:24:45+02:00
draft: true
---

Usando less +F como sustituto de tail -f
========================================

> Cuando necesitamos controlar un fichero de *log* casi siempre usamos `tail -f`. En mi caso ese `tail` a menudo va acompañado de un `grep`, abrir el fichero con un editor ...
>
> En este *post* veremos si es posible sustituir estos procesos con `less`.

Después de leer [Stop using tail -f (mostly)](http://www.brianstorti.com/stop-using-tail/) cada vez uso más la opción de `less +F`. En el se comentan las ventajas que presenta esta opción frente a `tail -f` cuando estamos revisando un archivo que está cambiando a lo largo del tiempo.

Además de este interesante post también podemos revisar ["tail -f" vs "less +F" : linux](https://www.reddit.com/r/linux/comments/4gzazs/tail_f_vs_less_f/)

Para mí, la **gran ventaja** de `less` sobre `tail` son las opciones de **navegación** y **búsqueda** que tiene el primero.

Es una ventaja pero hay que tener en cuenta una **diferencia importante** con respecto a `tail` y es que `tail -f` carga las **10 últimas** líneas del fichero más aquellas que se vayan sumando a lo largo del tiempo mientras que `less` **carga en memoria el contenido completo del fichero** que le estamos pasando. Esto puede ser problemático con ficheros grandes. Con estos ficheros tendremos problemas ya que `less` intentará calcular el número total de líneas y se quedará *"Calculating number line ...*". Podemos evitarlo pasándole el parámetro `-n` pero seguiremos cargando el fichero completo en memoria.

Ojo con esto, ya que `less` puede ser un *consumidor* importante de recursos si lo comparamos con `tail`. Incluso con pequeños ficheros podemos apreciar la diferencia (ver *gif* al final del post).

### Uso de `less`

Lanzamos `less` con la opción `+F` o lo lanzamos normalmente y pulsamos `F`. Con esto `less` pasa a *monitor mode*: nos vamos al final del archivo y `less` queda a la espera de cambios.

Aquí observamos una nueva diferencia con respecto a `tail -f` ya que este comando nos mostrará, en la mayoría de las plataformas [^1], los cambios de forma inmediata mientras que `less +F` **actualiza la salida cada segundo** (se observa claramente en el *gif* del final).

#### Scroll y búsqueda

En cualquier momento podemos salir al *modo normal* con `CTRL + c`. En este modo podemos:

-	Realizar búsquedas con `/` y movernos por los coincidentes con `N` y `n`.
-	Movernos por el fichero (con `j` y `k`por supuesto ;) )
-	Crear marcas con `m` + `letra`. Volveremos a la posición marcada pulsando `'letra`.
-	Editar el fichero pulsando `v`. Lanzamos el editor definido en la variable de entorno `VISUAL`.

Volveremos al *modo monitor* pulsando `F`. Obsevamos que si hicimos una búsqueda los coincidentes se siguen resaltando en las nuevas líneas que van apareciendo.

### Alternativas

Si no es posible el usar `less` y necesitamos alguna de sus características podemos utilizar `tail` con `tmux` o `screen`.

Algún *osado* usará un editor para estas tareas ... no lo hagas, usa `less +F`

### Gif resumen de lo mencionado en el post.

[![asciicast](https://asciinema.org/a/6dj5LUjh3hUiBKPztt9jkRTKN.png)](https://asciinema.org/a/6dj5LUjh3hUiBKPztt9jkRTKN)

[^1]: Si *inotify* está disponible `less` lo usará.
