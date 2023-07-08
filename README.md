# Página web del Proyecto CIAA

Este repositorio contiene el mirror de la página web del Proyecto Computadora Industrial Abierta Argentina.

La versión web se puede acceder desde la URL: https://mefhigoseth.github.io/ciaa-web/

## Cómo se hizo este Mirror ?

Para realizar el mirror se utilizó el siguiente comando:

```
$ wget --mirror --convert-links --adjust-extension --page-requisites --no-parent -X /devwiki/ http://www.proyecto-ciaa.com.ar/index.html
```

Luego se convirtió todos los links que apuntan al dominio `www.proyecto-ciaa.com.ar` a relativos, para que funcionen correctamente (aún cuando el sitio no esté hosteado en bajo este dominio):

```
$ find . -name '*.html' -exec sed -i -e 's/http:\/\/www.proyecto-ciaa.com.ar\//\//g' {} \;
```

Por último, convertimos todos los link que apuntan a la wiki a un anchor (#) para deshabilitarlos temporalmente:

```
$ find . -name '*.html' -exec sed -i -e 's/\/devwiki/#/g' {} \;
```