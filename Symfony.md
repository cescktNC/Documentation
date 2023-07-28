![Symfony Logo](/images/symfony_black.png)

# :blue_book: SYMFONY Documentation

**Symfony** es un framework de *php* creado en *php*. Con este framework se pueden hacer aplicaciones *Full Stack*. [Documentación oficial](https://symfony.com/doc/current/setup.html)

## Requisitos
### PHP y Composer
1. Instalar la última versión de [php](https://www.php.net/downloads).
2. Instalar [Composer](https://getcomposer.org/download/) para poder instalar paquetes de *php*.
3. Instalar  el comando *symfony* [Symfony CLI](https://symfony.com/download). Para windows hay que ejecutar el siguiente comando des de la terminal:
```bash
scoop install symfony-cli
```
### Verificar requisitos
Para comprobar si el ordenador cumple con los requisitos necesarios para poder crear aplicaciones en *symfony*, hay que ejecutar el siguiente comando en la terminal:
```bash
symfony check:requirements
```

## Crear un proyecto
Hay que usar el comando *symfony* y poner el **--webapp** para indicar a *symfony* que se trata de un proyecto web y de esta manera se instalará *twig* y una serie de paquetes necesarios. Hay que seguir la directrices que marca *symfony*, por tanto, el nombre del proyecto se tiene q separar con guiones bajos.
```bash
symfony new --webapp nombre_proyecto
```

## Ejecutar la aplicación
A diferencia de otros frameworks, *symfony* tiene un **servidor web local**, recomendado usar para desarrollo.
```bash
symfony server:start
```

## Controladores
Los controladores són parte de la arquitectura **MVC**. Són responsables de:
1. Manejar solicitudes o *Request en inglés* del cliente:
    * Datos enviador por un formulario.
    * Parámetros de la URL.
2. Interactuar con los *modelos* (para acceder y modificar datos).
3. Fnalmente devolver una respuesta al cliente:
    * Página *HTML* para mostrar al usuario.
    * Objeto *JSON* para una *API*.
    * *XML*.
    * Una descarga de un archivo.
    * Una redirección.
    * Un *error 404*.
    * o cualquier otro tipo de respuesta según las necesidades de la aplicación.

Ejemplo:
```php
namespace App\Controller;

use Symfony\Component\HttpFoundation\Response;
use Symfony\Component\Routing\Annotation\Route;

class LuckyController
{
    #[Route('/lucky/number/{max}', name: 'app_lucky_number')]
    public function number(int $max): Response
    {
        $number = random_int(0, $max);

        return new Response(
            '<html><body>Lucky number: '.$number.'</body></html>'
        );
    }
}
```
1. **namespace App\Controller;** :arrow_right: *Symfony* aprovecha la funcionalidad de los espacios de nombres **namespace** de PHP para poner el controlador completo en un espacio de nombres.
2. **use Symfony\Component\HttpFoundation\Response;** :arrow_right: *use* importa la clase **Response**, para que el controlador pueda devolver una respuesta *Response*.
3. **class LuckyController** :arrow_right: la clase puede tener cualquier nombre, pero por convención se le agrega el sufijo **Controller**.
4. **public function number(int $max): Response** :arrow_right: El método puede tener un argumento **$max** gracias al comodín *{max}* en la ruta.
5. **return new Response** :arrow_right: El controlador crea y devuelve un objeto *Response*.

### Generar un controlador
El siguiente comando, crea el controlador y su vista correspondiente:
```bash
php bin/console make:controller NombreController
```

## Gestion de paquetes
Para gestionar la instalación y desinstalación de paquetes en un proyecto, hay que usar el comando composer. El **--dev** es opcional y sirve para indicar que solamente se instale en el entorno de desarrollo.
```bash
composer require nombre_del_paquete --dev
```

### Paquete para generar código **maker-bundle** (Ya instalado por defecto, en entorno de desarrollo, al crear el proyecto).
```bash
composer require symfony/maker-bundle --dev
```
### Paquete para las anotaciones (validaciones de campos, etc).
```bash
composer require doctrine/annotations
```