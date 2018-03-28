---
title: "Montando un entorno para Oracle SQL-PL/SQL"
date: 2017-09-21T17:45:08+02:00
draft: true
---

## Motivación

Estaba recordando, de tiempos de estudiante, las maniobras que tenía que hacer para conseguir un entorno con el que poder estudiar la asignatura de _Oracle SQL_ y _PL/SQL_. A saber:

-	Hacer pasar la _Debian_ de turno por una _Red Hat_.
-	Variables de entorno, ampliar _swap_, arrancar aquel horrible instalador. [^1]
[^1]: [Oracle 8i on Linux RH7.X Installation HOWTO: Installing Oracle 8i, version 8.1.7](http://www.tldp.org/HOWTO/Oracle8-on-RH7X-HOWTO-3.html)
-	Rezar dos [Padre nuestro](https://es.wikipedia.org/wiki/Padre_nuestro) para que todo terminara sin incidentes.
-	Rezar dos [Avemarías](https://es.wikipedia.org/wiki/Avemar%C3%ADa) para que levantara el _listener_.
-	Crear una base de datos.
-	Por supuesto en este punto nos damos cuenta de que no elegimos instalar el _SQL*Plus_ con lo que tocaba volver al instalador. 
    
Después de todo esto ya no tenías tiempo ni ganas para estudiar.

## Vivan los contenedores

En este post intentaré describir los pasos para conseguir un pequeño entorno Oracle sobre el que, por ejemplo, podremos estudiar _PL/SQl_. Y en __menos de 5 minutos__!!!

Los requisitos previos serán tener un par de máquinas corriendo [Docker](https://www.docker.com/) y tener cuenta en [Docker Store](https://store.docker.com/).

Tenemos varias imágenes con las que disponer de gestor de base de datos _Oracle_ funcionando en un contenedor. En [Docker Hub](https://hub.docker.com/) encontraremos varias. Una de mis preferidas es [sath89/oracle-xe-11g - Docker Hub](https://hub.docker.com/r/sath89/oracle-xe-11g/)

Con esta imagen obtendremos una Oracle Express Edition 11g Release 2 ejecutándose sobre Ubuntu 14.04.1 LTS

Nos traemos la imagen 

```
docker pull sath89/oracle-xe-11g
```

Arrancamos un contenedor exponiendo el puerto _1521_ sin más. Tenemos alguna opción más pero como demostración nos sirve así.

```
docker run -d -p 1521:1521 sath89/oracle-xe-11g
```

Mientras se carga la imagen y arranca el contenedor, podemos ir descargando en otra máquina una imagen con el [Oracle Instant Client](http://www.oracle.com/technetwork/database/features/instant-client/index-097480.html).

Esta imagen la obtendremos del [Docker Store](https://store.docker.com/) con lo que tendremos que tener una cuenta, y agregar esta imagen a "_My Content_".

Seguimos las instrucciones que nos sugieren para obtener esta imagen __recordando__ hacer un `docker login` previo.

```
docker pull store/oracle/database-instantclient:12.2.0.1
```

A estas alturas ya tendremos el contenedor con la _Oracle Express Edition 11g_ corriendo con lo que podremos crear un contenedor con la imagen del _Oracle Instant Client_ y utilizarlo para conectarnos con la base de datos.

```
docker run -ti --rm store/oracle/database-instantclient:12.2.0.1 sqlplus system/oracle@192.168.0.3/xe
```

Todo el proceso en este gif.


[![asciicast](https://asciinema.org/a/FSCI1xOhFZqVGvjwVYZlr9jnq.png)](https://asciinema.org/a/FSCI1xOhFZqVGvjwVYZlr9jnq)

