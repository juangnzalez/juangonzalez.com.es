---
title: "Googler: googleando desde la línea de comandos"
date: 2017-10-11T18:42:08+02:00
draft: true
---

Del sitio web de [jarun/googler: Google Search, Google Site Search, Google News from the terminal](https://github.com/jarun/googler)

> Googler es una herramienta para consultar en Google (Web y News) desde la línea de comandos.
Muestra el título, URL y resumen de cada resultado, que se puede abrir directamente en un navegador.


## Principales características

- Se puede integrar con un __navegador basado en texto__.
- Podemos definir el __número de resultados a mostrar__ y desde qué posición se empezarán a mostrar.
- Limitar la __búsqueda por fecha__ de modificación o actualización.
- Búsqueda en un sitio utilizando ___Buscar en este Sitio___ de Google.
- Podemos elegir los __colores__ con los que se mostrarán los resultados.
- Auto-completado para _bash_, _fish_ y _zsh_.
- Podemos __desactivar la corrección automática__ para buscar por palabras clave exactas.
- Soporte para __palabras clave de Google__ como por ejemplo _filetype_.
- Podemos abrir el primer resultado directamente en el navegador (___I'm Feeling Lucky___).

 
## Instalación

Hemos de tener en cuanta que _googler_ necesita de _Python 3.3_ o superior.

Disponemos de paquetes con la última versión estable para _Arch_, _CentOs_, _Debian_, _Fedora_ y _Ubuntu_.

Para la instalación en _macos_ podemos optar por [Homebrew](https://brew.sh/index_es.html)

### Integración con nuestra shell

Mi shell es _zsh_ y utilizo _antigen_ para gestionar los módulos con lo que copiaré el [\_googler](https://github.com/jarun/googler/blob/master/auto-completion/zsh/_googler) que proporciona el autor en mi `~/.antigen/bundles/zsh-users/zsh-completions/src` y reinicio el `.zcompdump`

```bash
rm -f ~/.zcompdump; compinit
```

### Integración con un navegador

Definimos el navegador en el que se abrirán los resultados que obtendremos de _googler_  en la variable de entorno _BROWSER_.

Yo tengo `export BROWSER=lynx` en mi `~/.zshrc`

### Apariencia

Podemos personalizar los colores con los que se mostrarán los resultados asignando una __cadena de 6 caracteres__ a la variable de entorno `GOOGLER_COLORS` o pasándola como parámetro (`--colors`) al lanzar la aplicación.

Mi configuración es:

 - Índices de color magenta (f)
 - Títulos de color amarillo (y)
 - URLs de color azul (e)
 - Metadata (en Google News) en rojo (b)
 - Prompts en blanco _brillante_ (p)

lo que nos da una variable `GOOGLER_COLORS=flebhp`

Encontramos la __equivalencia entre caracter y color en la ayuda__ de la aplicación.

## Uso

Con `googler -h` o `man googler` obtendremos una pequeña descripción de los parámetros que le podemos pasar a la aplicación.

Alguna de las opciones que suelo utilizar son:

 - Obtener 3 resultados, actualizados en los últimos 5 meses, en castellano y utilizando [Google.es](https://www.google.es/):

```bash
googler -n 3 -t m5 -c es -l es prueba
```

 - Buscar ficheros en formato _pdf_:

 ```bash
googler filetype:pdf prueba
 ```

Podemos lanzarlo sin parámetros y usarlo de forma interactiva usando un _prompt_ que el autor denomina __omniprompt__. Opciones disponibles pulsando `?`


### Lector de noticias

También obtendremos un útil lector de noticias (_News de Google_) en modo _distracttion-free_ si lo combinamos con [zyocum/reader: Extract clean(er), readable text from web pages via Mercury Web Parser API.](https://github.com/zyocum/reader):

- Instalamos requerimientos [reader/requirements.txt at master · zyocum/reader](https://github.com/zyocum/reader/blob/master/requirements.txt) y descargamos el script _reader.py_ en un directorio que pertenezca a nuestro `PATH`.
- Nos registramos en [Mercury Web Parser](https://mercury.postlight.com/web-parser/) e instalamos un _parseador_ para _json_ como por ejemplo [jq](https://stedolan.github.io/jq/)
- Creamos un pequeño script (`reader`) con los parámetros necesarios para lanzar _reader.py_, le damos permisos de ejecución y nos aseguramos de que esté en un directorio del `PATH`

```bash
reader.py $1 -k "obtener APP KEY de Mercury Web Parser API" -w 80 | jq -r '[
    (if .title then "# "+.title else empty end),
    (if .author then .author else empty end),
    .content.text
] | join("\n\n")' | w3m
```

- Lanzamos nuestro lector de noticias_ con `googler -N -l es -c es -n 5 --url-handler reader noticias`

## Resumen

Y para terminar un pequeño resumen en formato gif.

[![asciicast](https://asciinema.org/a/K5M3KuIi2kGJ30qyaqvPdCTVm.png)](https://asciinema.org/a/K5M3KuIi2kGJ30qyaqvPdCTVm)
