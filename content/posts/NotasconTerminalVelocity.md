---
title: "Notas con Terminal Velocity"
date: 2017-09-27T17:33:07+02:00
draft: true
---

El sistema que uso para tomar y consultar notas se basa en __ficheros de texto__ con formato [Markdown](https://es.wikipedia.org/wiki/Markdown) alojados en un directorio [Dropbox](https://www.dropbox.com).

Desde hace años utilizo [Notational Velocity](http://notational.net/) o alguno de sus _derivados_. 

Existen bastantes aplicaciones que imitan la funcionalidad de _NV_; he probado muchas y mi preferida es [nvALT](http://brettterpstra.com/projects/nvalt/).

La inmensa mayoría de estas aplicaciones basadas en _NV_ son para entornos gráficos. Ando a la caza de una aplicación que funcione en la línea de comandos con funcionalidades parecidas a [Notational Velocity](http://notational.net/) y de momento la que más me gusta y la que últimamente más utilizo es [Terminal Velocity](https://www.seanh.cc/terminal_velocity/).

## Instalación y uso

La instalación es muy sencilla. Necesitamos el administrador de paquetes [Pip](https://es.wikipedia.org/wiki/Pip_(administrador_de_paquetes)) y nada más. 

Por ejemplo en una instalación de [DietPi](http://dietpi.com/) sobre una [Raspberry Pi Zero W](https://www.raspberrypi.org/products/raspberry-pi-zero-w/) empezamos con un: 

```bash
apt-get install vim python-pip python-dev
```

y continuamos con las instrucciones del sitio de la aplicación [Terminal Velocity](https://www.seanh.cc/terminal_velocity/).

```bash
pip install terminal_velocity
```
Ejecutamos con:

```bash
terminal_velocity
```

El funcionamiento es similar al de [Notational Velocity](http://notational.net/):

- Lanzamos [Terminal Velocity](https://www.seanh.cc/terminal_velocity/) en el directorio donde tengamos almacenadas las _notas_.
- Pulsamos `CTRL` + `L` y empezamos a escribir. Según vamos añadiendo caracteres la aplicación va realizando una búsqueda en __título__ y __contenido__ de nuestras notas. Nos movemos por los coincidentes con las teclas `ARRIBA` y `ABAJO` y seleccionamos uno con `ENTER`. Se abrirá el editor definido en la `$EDITOR` de nuestro entorno. Editamos o simplemente visualizamos la nota, salimos del editor y volvemos a la lista de coincidentes.
- Salimos de la aplicación con un `CTRL` + `C`.

Si queremos __crear una nota nueva__ terminamos de escribir el título de esta, no se mostrarán coincidentes, pulsamos `ENTER` y comenzamos a añadir el contenido en `$EDITOR`.

Para mi esta es la __funcionalidad más atractiva__ de [Notational Velocity](http://notational.net/) y creo que está __muy bien implementada__ en [Terminal Velocity](https://www.seanh.cc/terminal_velocity/) tal y como podemos ver en el _gif_ del final de este _post_.

### Configuración

Como siempre un `terminal_velocity --help` nos ayudará para ajustar la configuración de la aplicación a nuestras necesidades.

En un `~/.tvrc` podemos establecer el __editor__ que utilizaremos (prevalece sobre `$EDITOR`), la __extensión__ con las que se crearán nuestras notas, el __directorio por defecto__ en el que la aplicación buscará y creará las notas y alguna opción más.

### Sincronización

Las notas se crean en formato __texto plano__ con lo que es sencillo, a priori, encontrar una forma de __sincronizar el directorio__ que las contiene entre diferentes máquinas.

Digo _sencillo a priori_ ya que en mi caso no lo es tanto. 
Varias de las máquinas que utilizo tienen [arquitectura ARM](https://es.wikipedia.org/wiki/Arquitectura_ARM) pero el sistema de sincronización que vengo utilizando desde hace mucho es [Dropbox](https://www.dropbox.com/) que sólo tiene clientes para [x86](https://es.wikipedia.org/wiki/X86) con lo que necesito algo más de trabajo para mantener mis notas sincronizadas.

La solución evidente: dejar _Dropbox_, pero mientras me decido y no, vengo utilizando una mezcla de _Dropbox_ y _Git_ con la que voy tirando.

En las máquinas _ARM_ tengo instalado un estupendo script de _Bash_ [GitHub - andreafabrizi/Dropbox-Uploader](https://github.com/andreafabrizi/Dropbox-Uploader) con el que consigo las funcionalidades básicas para manejar ficheros en _Dropbox_. 

EL script está muy bien, hasta ofrece una _shell_ para interactuar con _Dropbox_.

Complemento este _script_ con [Git](https://es.wikipedia.org/wiki/Git).
En concreto utilizo un repositorio privado en [GitLab](https://gitlab.com/).

Al final consigo tener las notas sincronizadas con esta mezcla de _Dropbox_ y _GitLab_.
Cuando añado o edito en una _x86_ dejo a _Dropbox_ que se encargue y pongo al día el repositorio en _GitLab_. Si trabajo en una _ARM_ siempre he de acordarme de sincronizar antes y después.

Es un poco pesado pero funciona.

Resumen de todo lo comentado en el post en este _gif_.

[![asciicast](https://asciinema.org/a/PvXIpr9AccMYFoLxyUXE5SYcd.png)](https://asciinema.org/a/PvXIpr9AccMYFoLxyUXE5SYcd)
