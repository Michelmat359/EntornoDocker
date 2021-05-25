Plantilla de un stack php:7.2 + mysql + php-composer dockerizado.

## Contenido

### PHP

Imagen de php-7.2 con XDebug instalado. Tiene tambien instaladas las siguientes extensiones:
  - mbstring
  - zip
  - gd
  - intl
  - pdo_mysql

### Mysql

Imagen de MySQL:5.6

El archivo `bootstrap.sql` puede rellenarse en caso de que haga falta una base de datos.

Se ejecutará la primera vez que se contruya el contenedor de mysql.

### Composer

Imagen de php-composer.

Para poder instalar los paquetes de composer, se utiliza de la siguiente forma:

``` bash
docker-compose run composer composer install
```

### .env

Archivo de variables de entorno. Está definida la variable `COMPOSE_PROJECT_NAME`, que se usa en el `docker-compose.yml` para dar nombre a los servicios.
Si no se define el valor de la variable para el nombre del proyecto, por defecto usará el nombre de la carpeta que contiene el `docker-compose.yml`.
Es recomendable que los contenedores tengan un nombre único para evitar colisiones.


## Levantar el entorno


``` bash
docker-compose up -d --build
```

Nota: si lanzas el `docker-compose up` usando el parámetro `-f` (automático al lanzarlo desde visual code), ignora el valor de `COMPOSE_PROJECT_NAME` definido en el `.env`.

### Instalar Laravel (por ejemplo)

Para crear un proyecto de laravel, lanzar el comando a traves del contenedor de `composer`:

``` bash
docker-compose run composer composer create-project laravel/laravel ./ 6.8 --prefer-dist
```

El código se generará dentro de la carpeta `./src`.
