![Symfony Logo](/images/symfony_black.png)

# :blue_book: SYMFONY Documentation

**Symfony** es un framework de *php* creado en *php*. Con este framework se pueden hacer aplicaciones *Full Stack*. [Documentación oficial](https://symfony.com/doc/current/setup.html)

## Requisitos
### PHP y Composer
1. Instalar la última versión de [php](https://www.php.net/downloads).
2. Instalar [Composer](https://getcomposer.org/download/) para poder instalar paquetes de *php*.
### Verificar requisitos
Para comprobar si el ordenador cumple con los requisitos necesarios para poder crear aplicaciones en *symfony*, hay que ejecutar el siguiente comando en la terminal:
```
symfony check:requirements
```

## Crear un proyecto
Hay que usar el comando *symfony* y poner el **--full** para indicar a symfony que se trata de un proyecto completo y de esta manera se instalará twig y una serie de paquetes necesarios:
```
symfony new nombre_proyecto --full
```