![React Logo](/images/react_logo.png)
# :blue_book: REACT Documentation

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



added by Francesc
