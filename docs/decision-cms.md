# Decisión de imagen y versión del CMS

## Requisitos oficiales de WordPress
- PHP recomendado: (anota aquí)
- Base de datos recomendada: (anota aquí)
- HTTPS: (anota si lo exige o lo recomienda)

## Imagen elegida
`wordpress:7.1-php8.3-fpm`

## Justificación
- **fpm vs apache:** fpm solo ejecuta PHP y necesita un servidor web aparte (p. ej. Nginx); apache lo trae todo integrado.
- **php8.3:** versión de PHP incluida en la imagen.
- **No usar latest:** la etiqueta cambia con el tiempo y se pierde la reproducibilidad.

## Comprobaciones realizadas
- PHP: (pega aquí la salida de `php -v`)
- Módulos presentes: mysqli, gd, zip, intl, imagick
- Tamaño de la imagen: (pega aquí el dato de `docker image ls wordpress`)
