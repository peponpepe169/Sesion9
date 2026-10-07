# Decisión de imagen y versión del CMS

## Requisitos oficiales de WordPress
Fuente: https://wordpress.org/about/requirements/

- **PHP recomendado:** versión 8.3 o superior. WordPress todavía funciona con PHP 7.4+, pero esas versiones están fuera de soporte y pueden exponer el sitio a vulnerabilidades.
- **Base de datos recomendada:** MariaDB 10.11 o superior, o MySQL 8.0 o superior.
- **HTTPS:** sí, la página oficial indica que el servidor debe soportar HTTPS, para cifrar la conexión con el sitio.
- **Servidor web:** se recomienda Apache o Nginx (con el módulo mod_rewrite en el caso de Apache).

## Imagen elegida
`wordpress:7.1-php8.3-fpm`

## Justificación
- **fpm vs apache:** la variante `-apache` incluye Apache con PHP integrado y funciona sola. La variante `-fpm` solo ejecuta PHP-FPM y necesita un servidor web aparte (por ejemplo Nginx) que le pase las peticiones PHP. Elegimos `-fpm` porque permite separar el servidor web de PHP en contenedores distintos.
- **php8.3:** indica que la imagen trae PHP 8.3, que cumple el mínimo recomendado por WordPress.
- **Por qué no usar latest:** la etiqueta `latest` cambia con el tiempo, así que no se sabe qué versión de WordPress o PHP se obtiene. Fijar la versión garantiza que el entorno sea reproducible y que no se rompa por una actualización inesperada.
- **Licencia:** WordPress se distribuye bajo licencia GPL, que permite usarlo, modificarlo y redistribuirlo libremente.

## Comprobaciones realizadas

### Versión de PHP (`php -v`)
```
PHP 8.3.35 (cli) (built: Oct  6 2026 01:30:28) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.3.35, Copyright (c) Zend Technologies
    with Zend OPcache v8.3.35, Copyright (c), by Zend Technologies
```

### Módulos PHP necesarios presentes
```
gd
imagick
intl
mysqli
zip
```

### Imagen descargada (`docker image ls wordpress`)
```
IMAGE                      ID             DISK USAGE   CONTENT SIZE   EXTRA
wordpress:7.1-php8.3-fpm   ce765b661397        1.1GB          272MB        
```
