![Symfony Logo](/images/symfony_black.png)

# :blue_book: SYMFONY Documentation

**Symfony** es un framework de *php* creado en *php*. Con este framework se pueden hacer aplicaciones *Full Stack*. [Documentación oficial](https://symfony.com/doc/current/setup.html)

## Requisitos
### PHP y Composer
1. Instalar la última versión de [php](https://www.php.net/downloads).
2. Instalar [Composer](https://getcomposer.org/download/) para poder instalar paquetes de *php*.
3. Instalar  el comando *symfony* [Symfony CLI](https://symfony.com/download). Para windows hay que ejecutar el siguiente comando des de la terminal:
```
scoop install symfony-cli
```
### Verificar requisitos
Para comprobar si el ordenador cumple con los requisitos necesarios para poder crear aplicaciones en *symfony*, hay que ejecutar el siguiente comando en la terminal:
```
symfony check:requirements
```

## Crear un proyecto
Hay que usar el comando *symfony* y poner el **--webapp** para indicar a *symfony* que se trata de un proyecto web y de esta manera se instalará *twig* y una serie de paquetes necesarios. Hay que seguir la directrices que marca *symfony*, por tanto, el nombre del proyecto se tiene q separar con guiones bajos.
```
symfony new --webapp nombre_proyecto
```

## Gestion de paquetes
Para gestionar la instalación y desinstalación de paquetes en un proyecto, hay que usar el comando composer. El **--dev** es opcional y sirve para indicar que solamente se instale en el entorno de desarrollo.
```
composer require nombre_del_paquete --dev
```

### Paquete para generar código **maker-bundle** (Ya instalado por defecto, en entorno de desarrollo, al crear el proyecto).
```
composer require symfony/maker-bundle --dev
```
### Paquete para las anotaciones (validaciones de campos, etc).
```
composer require doctrine/annotations
```