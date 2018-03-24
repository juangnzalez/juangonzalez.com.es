---
title: "Usando Google Translate desde la línea de comandos"
date: 2018-03-24T11:54:58+01:00
draft: true
---

En este post comentaré el uso básico de dos aplicaciones con las que
podremos utilizar **Google Translate** para traducir palabras y oraciones desde
la línea de comandos.

## Trino, traducción fácil desde CLI.

[GitHub - eneserdogan/trino: Trino: Master your translations with command line!](https://github.com/eneserdogan/trino)

Esta es, de las dos, la más sencilla y con menor numero de
opciones pero no por ello menos
útil.

Según su autor, **trino** permite una rápida y fácil traducción de palabras y
frases desde la línea de comandos.

### Instalación.

Instalamos la aplicación desde el gestor de paquetes de **Node** [npm](https://www.npmjs.com/get-npm?utm_source=house&utm_medium=homepage&utm_campaign=free%20orgs&utm_term=Install%20npm)

```
npm install -g trino
```

### Uso

Al ejecutar **trino** se crea una *shell* en la que podemos lanzar dos
comandos.

- `trino [opciones] <texto> <objetivo>`.

La salida de este comando será `Translation: <resultado>`

Podemos completar los parámetros con los que lanzamos el programa con el
tabulador.

Por ejemplo `trino "Un ejemplo" [Tab][Tab]` nos mostrará todos los códigos
(2 caracteres) de los idiomas a los que podemos traducir la frase *Un
ejemplo*.

Como opciones tenemos `copy` que copia al porta papeles del sistema el
resultado de la traducción.

- `trino-dt <texto>`.

La salida será `Detect: <resultado>` siendo _resultado_ el idioma del
_texto_ que pasamos en la entrada.

## Translate Shell. Solución muy completa para traducciones desde CLI.

[GitHub - soimort/translate-shell: Command-line translator using Google Translate, Bing Translator, Yandex.Translate, DeepL Translator, etc.](https://github.com/soimort/translate-shell)

**translate shell** es un traductor para la línea de comandos que ofrece
acceso fácil a varios motores de traducción.

Estos motores son **Google Translate** (opción por defecto), **Bing
Translator**, **Yandex**, **DeepL Translator** y **Apertium**.

### Instalación.

Podemos clonar el repositorio en [**GitHub**](https://github.com/soimort/translate-shell), utilizar algún gestor de paquetes o la opción más rápida, bajarnos el ejecutable en un directorio de nuestro `PATH` desde *git.io/trans*. En mi sistema sería algo como:

```
printenv | grep PATH
cd /usr/local/bin
wget git.io/trans
chmod +x trans
```

### Uso 

**translate-shell** ofrece muchas opciones que van desde usar la
aplicación como un diccionario, identificar en qué lenguaje está una frase
o palabra que le pasamos, traducir un fichero o página web e incluso hacer
un *text-to-speech* con el resultado de la traducción que solicitemos.

- Traducir una palabra.

Este sería el uso básico de la aplicación.

```
trans test
```

traduce la palabra *test* al idioma definido en nuestra variable de
entorno `LANG`.

Para traducir una palabra a un idioma determinado lanzamos la aplicación con
`trans :fr prueba`

Podemos solicitar la traducción a más de un idioma concatenando sus
códigos con un *+*

```
trans :fr+en prueba
```

Para traducir una palabra especificando el idioma origen lo hacemos con un
`trans es: prueba`.

Podemos especificar idioma origen y destino para una traducción con

```
trans es:en prueba
```

- Traducir una frase.

Para traducir una frase la pasamos a la aplicación entrecomillada

```
trans :en "Una prueba de traducción"
```

- Modo resumen

El resultado de la traducción suele ser bastante extenso. Normalmente nos
servirá con el modo resumen.

```
trans -b :es hola
```

- Diccionario

**Google Translate** se puede usar como un diccionario si solicitamos la
traducción de una palabra al mismo idioma de esta, es decir

```
trans prueba
trans :es prueba
```

nos devolverá la definición de la palabra *prueba*.

También podemos forzar este comportamiento añadiendo la opción *d*

```
trans -d :es hola
```

- Text-to-speech

Podemos solicitar un *text-to-speech* pasando la opción *-play* 

```
trans -play "Una prueba"
```

y con *-speak* oiremos la palabra u oración que le pasemos

```
trans -speak "Hello, how are you?"
```

- Ficheros y páginas web

También podemos traducir ficheros de texto y páginas web

```
trans file://test.txt

trans https://www.w3.org/
```

- Shell

Una opción muy útil es crear una *shell* para ir traduciendo las palabras que
vayamos pasando.

Fijamos cuál será el idioma de entrada y cuál será el de salida

```
trans -shell es:en
```

## Resumen

Un pequeño *gif* resumen con lo más destacado de este *post*.

[![asciicast](https://asciinema.org/a/7E0mxK5fjXbWTGQIqySS4Uy2s.png)](https://asciinema.org/a/7E0mxK5fjXbWTGQIqySS4Uy2s)
