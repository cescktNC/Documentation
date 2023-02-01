![React Logo](/images/react_logo.png)
# :blue_book: REACT Documentation

**REACT** es un framework que se asegura de usar los recursos de la mejor manera. Esto es así porque
está constantemente comparando el *DOM virtual* con con el *DOM verdadero* y solo ejecuta los cambios
a los elementos específicos que han cambiado.
Por ejemplo, si tenemos un *div* con todo un listado de fotografias, en el momento que una de ellas
se actualiza por otra, el *DOM normal* cambiaria todo el *div* volviendo a mostrar todoas las fotografias,
donde ahora apareceria la nueva fotografia, en cambio, **REACT** solo cambiaria la fotografia que se
ha actualizado, y de esta manera se consumen menos recursos.

## Instalar React i ReactDOM:
Insertar dos **CDN's** en la página principal *HTML* del proyecto:

```javascript
<script crossorigin src="https://unpkg.com/react@18/umd/react.development.js"></script>
```

```javascript
<script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
```

## Crear un elemento:
Se usa el método **createElement** de *React*. Se le pasan 3 parámetros:
1. El elemento que se va a crear (puede ser una etiqueta de *HTML* o un *Componente* de React).
2. Atributos para el elemento que se va a crear, si no se pasa ninguno, se pone a null.
3. El texto que va dentro de la etiqueta de *HTML*.

Después hay que [insertarlo](#insertar-un-elemento-en-la-página-web) en la página web.

Ejemplo:

```javascript
const h1 = React.createElement("h1", null, "Hello, world!");
```

```javascript
const h1 = React.createElement("h1", {className: 'clase-de-css'}, "Hello, world2!");
```
## Insertar un elemento en la página web:
Se usa el método **render** de **ReactDOM**. Se le pasan 2 parámetros:
1. El elemento a insertar.
2. El elemento raiz donde se tiene que insertar y se usa directamente la API del DOM (document.getElementById).

Ejemplo:

```javascript
ReactDOM.render(h1, document.getElementById('root'));
```
## JSX:
Para utilizar JSX hay que instalar **BABEL**. Para eso hay que insertar el **CDN** en la página principal del proyecto:

```javascript
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
```

En un proyecto real, no es una buena idea incluir **BABEL** en el proyecto porque es una libreria que ocupa mucho. Es mejor escribir en *JSX*, después utilizar *BABEL* para transformar *JSX* en *JavsScript* y de esta forma sólo se utiliza *JavaScript* en el proyecto y ocupará menos.

**JSX** sirve para poder escribir directamente *HTML* en el código de *JavaScript*, por tanto, la libreria **BABEL** lo que hace es compilar el codigo y transformarlo a *JavScript*. Para que compile el código, hay que ponerlo dentro de la siguiente etiqueta:

```javascript
<script type="text/babel">
    const h1 = <h1 className='clase-de-css'>Hola Mundo</h1>;
    ReactDOM.render(h1, document.getElementById('root'));
<script>
```
De esta manera, ya no haria falta crear un elemento de HTML con el método *createEelement*.
## Componentes:
React te permite crear tus propias etiquetas de HTML llamados **componentes**, dándoles tus propios estilos. Por ejemplo, puedes crear un botón con unos estilos en concreto, y despues, este componente lo puedes utilizar en muchas partes de un proyecto.
Los componentes se pueden crear de dos formas:
1. Creando una fucnión:

Los nombres de las funciones empiezan en **mayúscula**.

Ejemplo 1:
```javascript
function Bienvenido() {
    return <h1>Bienvenido</h1>;
}
ReactDOM.render(<Bienvenido />, document.getElementById('root'));
```
Ejemplo 2:
```javascript
function Bienvenido() {
    return <h1>Bienvenido</h1>;
}
const componente = <Bienvenido />;
ReactDOM.render(componente, document.getElementById('root'));
```
2. Creando una clase (Hoy en dia ya no se usa):

La clase que definimos siempre hereda de la clase componente *React.Component*.
```javascript
class Bienvenido extends React.Component {
    render() {
        return <h1>Bienvenido {this.props.nombre}</h1>;
    }
}
ReactDOM.render(<Bienvenido nombre="Charly" />, document.getElementById('root'));
```

### Componentes (Propiedades)
Una etiqueta *HTML* tiene atributos y lo mismo se puede hacer con los *componentes*, que se conocen como propiedades.
Ejemplo:
```javascript
function Bienvenido(props) {
    return <h1>Bienvenido {props.nombre}</h1>;
}
const app = (
    <div>
        <Bienvenido nombre="Pedro"/>
        <Bienvenido nombre="Luis"/>
    </div>
);
ReactDOM.render(app, document.getElementById('root'));
```
### Componentes (Eventos)
Un evento se puede crear tanto en un componente de tipo función como de tipo clase. Dos ejemplos con el evento *onClick*:
1. Evento en componente de tipo función:
```javascript
function Alertador(props) {
    return (
        <div>
            <button onClick={() => alert('Alerta!')}>Click!</button>
        </div>
    );
}
ReactDOM.render(<Alertador />, document.getElementById('root'));
```
2. Evento en componente de tipo clase:
```javascript
class Alertador extends React.Component {
    render() {
        return (
            <div>
                <button onClick={this.onClick}>Click!</button>
            </div>
        );
    }
}
ReactDOM.render(<Alertador />, document.getElementById('root'));
```
### Componentes (Estado)
Al igual que las etiquetas *HTML*, los componentes también tienen un estado. Por ejemplo, un checkbox en *HTML* cuando cambia a *checked*, significa que su estado interno cambia. Otro ejemplo seria un *input*, en el momento que se introduce texto, su estado cambia porque se está añadiendo texto en el value.
En el estado de un componente se puede guardar lo que se quiera y se puede guardar mucha información, o simplemente un *true* o *false* para cambiar la forma visual del componente.
Un estado se puede crear tanto en un componente de tipo función como de tipo clase. Para crear un estado se usa el *hook (gancho)* **useState(valor_inicial)**. El valor que se le pasa por parámetro és el estado inicial. Este hook devuelve una lista con dos valores, el primero es el valor del estado y el segundo es una función que nos va a permitir cambiar el estado. 
1. Estado en componente de tipo función:
```javascript
function Contador(props) {
    const [contar, setContar] = React.useState(0); 

    return (
        <div>
            <h1>{contar}</h1>
            <button onClick={() => setContar(contar + 1)}>Click!</button>
        </div>
    );
}
ReactDOM.render(<Contador />, document.getElementById('root'));
```
2. Estado en componente de tipo clase:
```javascript
class Contador extends React.Component {
    constructor(props) {
        super(props);
        this.state = { contar: 0 };
    }

    render() {
        return (
            <div>
                <h1>{this.state.contar}</h1>
                <button onClick={() => this.setState((state, props) => ({ contar: state.contar + 1 }))}>Click!</button>
            </div>
        );
    }
}
ReactDOM.render(<Contador />, document.getElementById('root'));
```

added by Francesc
