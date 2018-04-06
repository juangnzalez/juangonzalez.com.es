---
title: "Consultando el pronóstico del tiempo desde CLI"
date: 2018-04-05T19:16:23+02:00
draft: true
---

> En este *post* comentaré las características principales de la aplicación
> que utilizo para consultar la previsión del tiempo atmosférico desde la
> **línea de comandos**.

Tenemos muchas opciones para esta tarea pero mi preferida es [GitHub - schachmat/wego: weather app for the terminal](https://github.com/schachmat/wego)

## Características.

- Podemos consultar la previsión del tiempo para hasta 7 días (dependerá del
  proveedor y las características de la cuenta que utilicemos).
- Iconos en modo texto (*ASCII art*).
- Muestra temperatura real y sensación térmica (por supuesto si el proveedor
  proporciona el dato).
- Muestra la probabilidad de lluvia.
- Soporte (parcial) del castellano.

## Dependencias.

Antes de instalar la aplicación debemos tener resueltas las dependencias.

- [The Go Programming Language](https://golang.org/) instalado en nuestro
  entorno.
- Lanzaremos la aplicación desde un emulador de terminal con soporte **utf-8*,
  **256 colores**.
- Acceso a al **API** con la *API key* correspondiente del proveedor que
  elijamos entre los tres posibles:

  1. [Dark Sky](https://darksky.net/dev)
  2. [Weather API | Local Weather API | World Weather
     Online](https://developer.worldweatheronline.com/api/) que parece ser ya
     no proporciona acceso gratuito a su API.
  3. [Weather API - OpenWeatherMap](https://openweathermap.org/api) **mi
     elección**.

### [OpenWeatherMap](https://openweathermap.org/)

Creamos una cuenta en [Members](https://home.openweathermap.org/) y accedemos a
la clave de acceso a la **API** en
[Members](https://home.openweathermap.org/api_keys).

Al registrarnos obtendremos acceso gratuito a la predicción del tiempo para 5
días.

## Instalación.

Una vez resueltas las dependencias podemos instalar la aplicación con un:

```bash
go get -u github.com/schachmat/wego
```

Hemos de comprobar que tenemos la variable de entorno `GOPATH` correctamente
definida.

## Configuración y uso.

Al ejecutar por primera vez la aplicación se creará en nuestro `home` un
fichero `.wegorc` en el cual definiremos el proveedor que vamos a utilizar,
número de días para los que queremos obtener la previsión del tiempo, idioma en
el que se mostrarán los datos, localización para la que solicitamos la
previsión y la clave de acceso a la *API* del proveedor elegido.

Con todos los parámetros definidos ejecutamos de nuevo la aplicación con un
`wego` y se nos mostrará en la terminal los datos del tiempo en la ubicación
definida en el fichero de configuración para el día
actual además de la previsión para los próximos días.

Obtendremos para cada día las condiciones meteorológicas que se prevén en
cuatro momentos del día: mañana, mediodía, tarde y noche.

## Resumen.

Para terminar un pequeño gif resumen de lo comentado.

[![asciicast](https://asciinema.org/a/AyobM5uk7yr6H66bI6vEd70TB.png)](https://asciinema.org/a/AyobM5uk7yr6H66bI6vEd70TB)
