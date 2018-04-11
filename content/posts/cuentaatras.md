---
title: "Cuenta atrás desde la Línea de Comandos"
date: 2018-04-11T18:46:02+02:00
draft: true
---

> En este post está dedicado a la aplicación que uso como *temporizador*.

[GitHub - trehn/termdown: Countdown timer and stopwatch in your
terminal](https://github.com/trehn/termdown) funciona
como cronómetro o como temporizador. Esta última aplicación es la que uso con más
frecuencia.

Para mí la característica más importante es que podemos tener hasta 3 métodos
con los que se nos informará del fin de la cuenta atrás que hayamos definido.

## Instalación.

[Termdown](https://github.com/trehn/termdown) es una aplicación escrita en
[Python](https://www.python.org/). Podemos instalarla con el
gestor de paquetes de este lenguaje [Pip](https://es.wikipedia.org/wiki/Pip_(administrador_de_paquetes)).

Con un simple `pip install termdown` tendremos la aplicación instalada en
nuestro sistema.

## Uso

Obtendremos las opciones o parámetros que podemos pasarle a la aplicación con
un `termdown --help`.

Como comentaba al principio la opción de usar la aplicación como temporizador o
cuenta atrás es la que uso.

Para mí los parámetros más interesantes son:

- `-b, --blink` cuando termina la *cuenta atrás* se genera un *parpadeo* en la
  terminal (ver [gif](https://asciinema.org/a/1kd5SF7pK0etd36FmBDVIpJ6g)
  final).
- `-c, --clitical N` Cuando el contador llega a los `N` segundos finales el
  contador pasa a color rojo.
- `-q, --quit-after N` después de `N`segundos se finaliza el *blink* definido
  con la opción `-b`.
- `-T, --title TEXTO` texto a mostrar en la parte superior de nuestro
  temporizador.
- `-v, --voice VOICE` oiremos la cuenta atrás final con la voz que definamos en
  `VOICE`. Para saber qué *voces* tenemos disponibles en *macOS* ejecutamos `say -v '?'`. En castellano (*es_ES*) disponemos de las voces de *Jorge* y *Mónica*.

### Teclas

Durante la ejecución podemos utilizar las siguientes teclas para controlar la
aplicación.

- `l` marcamos el fín de una *vuelta* cuando estamos en modo *cronómetro*
- `r` hacemos un *reset*
- `espacio` hacemos una *pausa*
- `q` salimos de la aplicación 

## Resumen

Cuando termine la cuenta atrás podemos conseguir tres avisos:

- Con el parámetro `b` se mostrará un parpadeo rojo en la terminal desde la que
  lanzamos la aplicación.
- Con el `-v [Jorge, Monica]` oiremos la cuenta atrás final. Por ejemplo si
  lanzamos un temporizador de un minuto con un `-c 3` se nos informará de que
  hemos llegado a los 30 últimos segundos, a los 10 últimos, a los 5 y
  finalmente oiremos el 3, 2, 1 final.
- A no ser que especifiquemos lo contrario pasando el parámetro `-B` la
  conclusión de la cuenta atrás siempre genera un `BELT` en nuestra consola con
  lo que lo más seguro es que también obtengamos un avisó por el sistema de
  notificaciones de nuestro sistema.

Así es seguro que nos enteraremos del final de la cuenta atrás.

Y como siempre un pequeño gif demostración.

[![asciicast](https://asciinema.org/a/1kd5SF7pK0etd36FmBDVIpJ6g.png)](https://asciinema.org/a/1kd5SF7pK0etd36FmBDVIpJ6g)
