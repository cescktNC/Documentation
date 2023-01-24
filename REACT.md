![React Logo](/images/react_logo.png)
# :blue_book: REACT Documentation

REACT es un framework que se asegura de usar los recursos de la mejor manera. Esto es así porque
está constantemente comparando el DOM virtual con con el DOM verdadero y solo ejecuta los cambios
a los elementos específicos que han cambiado.
Por ejemplo, si tenemos un div con todo un listado de fotografias, en el momento que una de ellas
se actualiza por otra, el DOM normal cambiaria todo el div volviendo a mostrar todoas las fotografias,
donde ahora apareceria la nueva fotografia, en cambio, REACT solo cambiaria la fotografia que se
ha actualizado, y de esta manera se consumen menos recursos.

## Instalar React i ReactDOM:
Insertar dos **CDN's** en la página principal *HTML* del proyecto:

```<script crossorigin src="https://unpkg.com/react@18/umd/react.development.js"></script>```

```<script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>```

## Crear un elemento:
Se usa el método **createElement** de *React*. Se le pasan 3 parámetros:
1. El elemento que se va a crear (puede ser una etiqueta de *HTML* o un *Componente* de React).
2. Atributos para el elemento que se va a crear, si no se pasa ninguno, se pone a null.
3. El texto que va dentro de la etiqueta de *HTML*.

Después hay que [insertarlo](#insertar-un-elemento-en-la-página-web) en la página web.

Ejemplo:

```const h1 = React.createElement("h1", null, "Hello, world!");```

```const h1 = React.createElement("h1", {className: 'clase-de-css'}, "Hello, world2!");```
## Insertar un elemento en la página web:
Se usa el método **render** de **ReactDOM**. Se le pasan 2 parámetros:
1. El elemento a insertar.
2. El elemento raiz donde se tiene que insertar y se usa directamente la API del DOM (document.getElementById).

Ejemplo:

```ReactDOM.render(h1, document.getElementById('root'));```
## JSX:
Para utilizar JSX hay que instalar **BABEL**. Para eso hay que insertar el **CDN** en la página principal del proyecto:

```<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>```

En un proyecto real, no es una buena idea incluir **BABEL** en el proyecto porque es una libreria que ocupa mucho. Es mejor escribir en *JSX*, después utilizar *BABEL* para transformar *JSX* en *JavsScript* y de esta forma sólo se utiliza *JavaScript* en el proyecto y ocupará menos.

**JSX** sirve para poder escribir directamente *HTML* en el código de *JavaScript*, por tanto, la libreria **BABEL** lo que hace es compilar el codigo y transformarlo a *JavScript*. Para que compile el código, hay que ponerlo dentro de la siguiente etiqueta:

```
<script type="text/babel">
    const h1 = <h1 className='clase-de-css'>Hola Mundo</h1>;
    ReactDOM.render(h1, document.getElementById('root'));
<script>
```
De esta manera, ya no haria falta crear un elemento de HTML con el método *createEelement*.

added by Francesc
