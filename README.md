# Prestashop Docker

Este proyecto ofrece un conjunto de servicios con los cuales podemos echar a andar una
tienda online en Prestashop en cuestión de minutos.

## Para empezar

Por favor, sigue las instrucciones que se detallan a continuación para que todo funcione
correctamente y no te saltes ningún paso.

Si tienes sugerencias de mejora y crees que se puede optimizar algo en el proceso y/o código
o simplemente tienes dudas, ponte en contacto conmigo.

### Requisitos

Para poder ejecutar el proyecto, necesitamos tener en nuestra máquina los siguientes
requerimientos:

- Instalación de [Docker](https://www.docker.com/).
- Instalación de [Docker Compose](https://docs.docker.com/compose/).

### Proceso de instalación

Descargamos el proyecto en zip o por haciendo uso de git.

```
git@gitlab.com:AbrahanZarza/prestashop-docker.git
```

Nos movemos hasta el directorio raíz del proyecto y una vez allí, arrancamos los servicios de docker.

```
cd your_path/prestashop-docker
docker-compose up -d --build
```

> Este comando nos creará las imágenes y contenedores necesarios para arrancarlo todo. Si no teníamos los recursos,
él sólo los creará.

Esperamos un par de minutos aproximadamente y ya tendremos el proyecto accesible desde el navegador web.

```
http://localhost:8080
```

Si no teníamos Prestashop instalado en nuestro proyecto previamente, nos saldrá el asistente de instalación.
Sólo tendremos que rellenar los datos de nuestra tienda, pero hay que prestar especial atención al configurar
la conexión a la base de datos, cuyos parámetros se indican a continuación.

```
Host: mysql
User: root
Password: root
Database: prestashop
```

El resto es seguir los pasos y terminar de instalar.

## Pruebas

Para acceder a las distintas áreas de la tienda y explotar todo su potencial, sigue estas recomendaciones.

### Acceso al Front Office

Para acceder a la parte visible por los clientes de nuestra tienda, lo haremos desde la siguiente url.

```
http://localhost:8080
```

### Acceso al Back Office

Para acceder al panel de administración de la tienda, lo haremos desde la siguiente dirección web.

```
http://localhost:8080/ps-admin
```

## Errores reconocidos

#### AdminImportController.php

Hay un bug en la versión 1.7 de Prestashop que nos impide realizar cambios desde el Back Office. Es decir, guardar
productos, cambiar precios, características, etc. Es como si estuviese bloqueado.

Es un bug muy sencillo de arreglar. Una vez instalado prestashop, abrimos el fichero que se encuentra en esta ruta 
del proyecto.

```
/src/controllers/admin/AdminImportController.php
```

Y establecemos el valor de de la constante **`_PS_MODE_DEMO_`** como a `false`.

```
define('_PS_MODE_DEMO_', false);
```

Esto desactivará el modo demostración de la tienda, que es lo que la bloquea, y así podremos hacer cambios en el 
panel de administración.


## Construido con

- [Docker](https://www.docker.com/) - Software para contenerización.
- [Docker Compose](https://docs.docker.com/compose/) - Wrapper para Docker.
- [Prestashop](https://rometools.github.io/rome/) - Software CMS para E-commerce. 

## Autores

* [Abrahan Zarza](https://abrahanzarza.com) - *Proyecto inicial*

## Licencia

Este proyecto está abierto al uso de cualquier desarrollador que tenga valentía para adentrarse en el mundo de
Prestashop ;)

## Conocimientos recomendados

* PHP
* Smarty
* Symfony