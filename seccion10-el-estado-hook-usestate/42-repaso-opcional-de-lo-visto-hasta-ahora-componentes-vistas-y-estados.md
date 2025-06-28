# 42. Repaso OPCIONAL de lo visto hasta ahora componentes, vistas y estados

## Trabajar con React

* Editor de código recomendado: **Visual Studio Code**
* Extensión: **ES7+ React/Redux/React-Native snippets** de **dsznajder**
* **Node.js**

## Instalar React

Abrimos el CMD o terminal de nuestro sistema, y nos dirigimos a la carpeta donde queremos trabajar:

```bash
cd /ruta/donde/queremos/trabajar
```

Y ejecutamos:

```bash
npx create-react-app repaso-react
```

Para que cree el proyecto e instale todas las dependecias.

Una vez termianda la descarga, entramos a la carpeta del proyecto:

```bash
cd repaso-react
```

Y arrancamos nuestro proyecto:

```bash
npm start
```

## Carpetas en React

* `public/`: Es la que tiene el HTML, los logotipos, tod lo que se va a cargar de manera pública directamente.
* `public/index.html`: Tenemos el `<div id="root">` donde se carga la aplicación.
* `node_modules/`: Tenemos todas las dependencias.
* `src/`: Donde vamos a estar trabajando.

## Archivos irrelevantes (por ahora)

Eliminamos los archivos:

* `setupTests.js`
* `reportWebVitals.js`
* `App.test.js`

Y eliminamos las referencias a estos archivos en el `index.js`, y también quitamos el modo estricto (`<React.StrictMode>`):

```jsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
import App from './App';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <App />
);
```
## Componente principal `App.js`

Ahora, entramos al `App.js` que es el componente principal:

```jsx
import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}

export default App;
```

Que es el que vemos cargado por pantalla y sobre el que vamos a cargar otros componentes dentro.

## Definición de componente

Es una parte de la interfaz de la aplicación, o puede ser una página independiente, pero al final va a ser una parte de nuestra aplicación.

Al final se traduce en que es una función que renderiza algo por pantalla.

Por ejemplo, ahora mismo tenemos un componente que es el `App.js` y lo único que hace es mostrarnos lo que vemos actualmente por pantalla, pero
podríamos modificarlo.

## Modificando `App.js`

Podríamos quitar lo que tenemos y meter un párrafo:

```jsx
function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>Esto es un repaso de React con Víctor Robles</p>
      </header>
    </div>
  );
}
```

Y automáticamente nos actualiza eso en el navegador. Al estar corriendo nuestro proyecto de React, esto tiene un **auto-refresh** de cada cambio
que hagamos, tiene un **watcher** que comprueba cada cambio que hacemos, y actualiza la pantalla automáticamente.

## Creando componentes

Podemos crear componentes directamente dentro de `src/`, pero es mejor tener un folder donde tengamos los componentes.

Creamos un folder llamado `components/`. Dentro de esta carpeta tendremos los diferentes componentes.

Creamos los componentes

1. `PrimerComponente.js`
2. `SegundoComponente.js`

En VS Code, usamos el atajo `rafc` para definir el componente (**solo si hemos instalado la extensión mencionada al principio**), y nos creará lo que tiene que tener un componente por defecto.

`PrimerComponente.js`:

```jsx
import React from 'react'

export const PrimerComponente = () => {
  return (
    <div>PrimerComponente</div>
  )
}
```

`SegundoComponente.js`:

```jsx
import React from 'react'

export const SegundoComponente = () => {
  return (
    <div>SegundoComponente</div>
  )
}
```

Los componentes son funciones que devuelven una renderización por pantalla, al final devuelven un trozo de HTML.

Agregando HTML a `PrimerComponente.js`:

```jsx
export const PrimerComponente = () => {
  return (
    <div>
        <h1>Mi primer componente</h1>
        <p>Esto es un texto en mi componente</p>
    </div>
  )
}
```

Agregando HTML a `SegundoComponente.js`:

```jsx
export const SegundoComponente = () => {
  return (
    <div>
        <h2>Segundo componente</h2>
        <ul>
            <li>Dato 1</li>
            <li>Dato 2</li>
            <li>Dato 3</li>
        </ul>
    </div>
  )
}
```

Si revisamos el navegador ahora mismo no veremos nada. Y esto es porque cada componente es independiente y lo tendríamos que cargar dentro de
nuestro componente principal:

## Cargando componente dentro de `App.js`

VS Code importa los componentes automáticamente.

Cada componente tiene una etiqueta, que tiene el mismo nombre que el componente:

```jsx
import { PrimerComponente } from './components/PrimerComponente';
import { SegundoComponente } from './components/SegundoComponente';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>Esto es un repaso de React con Víctor Robles</p>

        <PrimerComponente />
        <hr />

        <SegundoComponente />
      </header>
    </div>
  );
}
```

Como no estamos devolviendo una función por default, lo que tenemos que hacer es utilizar las llaves para cargar el componente, que al final es
una función.

Si nos vamos al navegador, veremos los componentes ppor pantalla.

Los componentes los podemos reutilizar las veces que queramos:

```jsx
import logo from './logo.svg';
import './App.css';
import { PrimerComponente } from './components/PrimerComponente';
import { SegundoComponente } from './components/SegundoComponente';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>Esto es un repaso de React con Víctor Robles</p>

        <PrimerComponente />
        <PrimerComponente />
        <PrimerComponente />
        <PrimerComponente />
        <hr />

        <SegundoComponente />
      </header>
    </div>
  );
}
```

Podemos llamar al compponente las veces que queramos, al igual que haríamos con una función normal en JavaScript.

También podemos mostrar `PrimerComponente.js` dentro de `SegundoComponente.js`:

```jsx
import { PrimerComponente } from './PrimerComponente'

export const SegundoComponente = () => {
  return (
    <div>
        <h2>Segundo componente</h2>
        <ul>
            <li>Dato 1</li>
            <li>Dato 2</li>
            <li>Dato 3</li>
        </ul>

        <PrimerComponente />
    </div>
  )
}
```

## Pasar variables desde nuestro componente a nuestra template o vista

Creamos una variable o constante:

```jsx
let nombre = "Víctor";
let web = "victorroblesweb.es";
```

Estos son datos de una variable que en cualquier momento pueden cambiar. Los podríamos mostrar por pantalla, para ello, utilizamos las llaves `{}`. Con esto, estamos **interpolando**, es decir, tomar una variable de
nuestro componente y mostrarla/interpolarla dentro de otro `string`:

```jsx
export const PrimerComponente = () => {
    let nombre = "Víctor";
    let web = "victorroblesweb.es";

  return (
    <div>
        <h1>Mi primer componente</h1>
        <p>Esto es un texto en mi componente</p>
        <p>Mi nombre es: {nombre}</p>
        <p>Mi web es: {web}</p>
    </div>
  )
}
```

Veremos los datos por pantalla. Al venir de una variable, si hacemos cambiamos:

```jsx
let nombre = "Víctor Robles";
let web = "victorroblesweb.es";
```

Se va a reflejar por pantalla ese cambio.

Si tenemos una variable de tipo `array`:

```jsx
let cursos = [
  "Master en JavaScript",
  "Master en PHP",
  "Master en React",
  "Master en CSS"
];
```

Para mostrar los cursos, ya que lo que estamos aquí es **JSX**, es decir, HTML mezclado con JavaScript, podemos utilizar la gran parte de
cosas que conocemos de JavaScript dentro de nuestra template y utilizarlo como lenguaje de plantillas.

Entonces, para recorrer los cursos, abrimos llaves `{}` y ejecutar algo de JavaScript. Usamos la función `map()` de JavaScript, para recorrer o iterar un `array` cualquiera.

En cada iteración del `array` de `cursos`, vamos a hacer un `return` para imprimir el curso en un trozo de HTML. Para devolver HTML usamos los
paréntesis `()`:

```jsx
export const PrimerComponente = () => {
    let nombre = "Víctor";
    let web = "victorroblesweb.es";

    let cursos = [
        "Master en JavaScript",
        "Master en PHP",
        "Master en React",
        "Master en CSS"
    ];

  return (
    <div>
        <h1>Mi primer componente</h1>
        <p>Esto es un texto en mi componente</p>
        <p>Mi nombre es: {nombre}</p>
        <p>Mi web es: {web}</p>

        <h2>Cursos</h2>
        <ul>
            {
                cursos.map( curso => {
                    return (<li>
                        {curso}
                    </li>)
                })
            }
        </ul>
    </div>
  )
}
```

Veremos los cursos por pantalla sin ningún problema. Pero si revisamos la consola del navegador, tendremos un error:
`Each child in a list should have a unique "key" prop`.
Y es que cada elemento que iteramos dentro de una template debe tener una `key`.

Entonces, vamos a ponerle el atributo `key`, el índice lo pasamos cómo parámetro del callback que tiene la función `map()`:

```jsx
export const PrimerComponente = () => {
    let nombre = "Víctor";
    let web = "victorroblesweb.es";

    let cursos = [
        "Master en JavaScript",
        "Master en PHP",
        "Master en React",
        "Master en CSS"
    ];

  return (
    <div>
        <h1>Mi primer componente</h1>
        <p>Esto es un texto en mi componente</p>
        <p>Mi nombre es: {nombre}</p>
        <p>Mi web es: {web}</p>

        <h2>Cursos</h2>
        <ul>
            {
                cursos.map( (curso, indice) => {
                    return (<li key={indice}>
                        {curso}
                    </li>)
                })
            }
        </ul>
    </div>
  )
}
```

De esta manera, ya no tendremos ese error.

## Estados en React

Para esto vamos a utilizar el **hook** `useState`, uno de los hooks más importantes.

Si queremos cambiar el nombre que tenemos guardado en la variable `nombre`. Tendremos un botón que nos permita cambiar ese nombre y
utilizaremos el evento `onClick`.

Con el evento `onClick`, podemos ejecutar una función, que se llame `cambiarNombre()`. Para eso le pasamos el evento y ejecutamos la función
`cambiarNombre()`. Tambien definimos la función anónima con una constante llamada `cambiarNombre`, es la manera más óptima de definir las
funciones dentro de un componente de React:

```jsx
export const PrimerComponente = () => {
    let nombre = "Víctor";
    let web = "victorroblesweb.es";

    let cursos = [
        "Master en JavaScript",
        "Master en PHP",
        "Master en React",
        "Master en CSS"
    ];

    const cambiarNombre = (nuevoNombre) => {
        nombre = nuevoNombre;
    }

  return (
    <div>
        <h1>Mi primer componente</h1>
        <p>Esto es un texto en mi componente</p>
        <p>Mi nombre es: {nombre}</p>
        <p>Mi web es: {web}</p>

        <button onClick={ e => cambiarNombre("VICTOR ROBLES WEB") }>
            Cambiar nombre
        </button>

        <h2>Cursos</h2>
        <ul>
            {
                cursos.map( (curso, indice) => {
                    return (<li key={indice}>
                        {curso}
                    </li>)
                })
            }
        </ul>
    </div>
  )
}
```

Lo que esperaríamos es que se cambiara automáticamente el nombre que aparece por pantalla.

Pero si le damos clic al botón, no pasa nada.

El tema es que dentro de React tenemos que usar para esto Estados. Un **Estado**, es como una variable que está sujeta a cambios, que está
sujeta a la reactividad que tiene React.

Es decir, si queremos cambiar un valor y que automáticamente se refleje por pantalla, tenemos que utilizar un estado.

Lo que tendríamos que hacer primero es importar `useState`, que es el hook que vamos a usar y que proviene de React:

```jsx
import React, {useState} from 'react'
```

Para utilizarlo, nos creamos una variable y utilizamos la **desestructuración de array**, es decir, definirla con corchetes `[]` y
tendremos el nombre de este estado, y luego, el nombre de la función que va a cambiar ese estado, suelen llamarse `set+nombre_de_la_variable_o_estado`,
y comentaremos la variable `nombre` para que no haya conflicto.

Y le damos el valor de `useState`, una llamada a la función `useState`, y le ponemos un valor por defecto:

```jsx
// let nombre = "Víctor Robles";

const [nombre, setNombre] = useState("Víctor");
```

Y eso se va a mostrar por pantalla, proveniente del estado.

Ahora, para cambiar el valor del estado con el botón, usamos la función que nos permite hacer eso:

```jsx
const cambiarNombre = (nuevoNombre) => {
  setNombre(nuevoNombre);
}
```

De esta manera, cuando demos clic se ejecuta una función de callback que ejecuta a `cambiarNombre()`. Si lo comprobamos en el navegador, nos
cambia automáticamente el nombre.

## Evento onChange

También podemos tenr un `<input>` que tenga el evento `onChange`. Este evento captura cualquier cambio que haya dentro del `<input>`. Es decir,
mientras que modifiquemos el valor del `<input>`, lo que haremos es ejecutar una función.

Ejecutaremos una función de callback que va a recibir el evento en sí, y ejecutaremos `cambiarNombre()`, pero le pasaremos el valure que tenga este campo de texto, el `target` del evento actual, y su `value`:

```jsx
<input type="text" onChange={e => cambiarNombre(e.target.value)} placeholder="Cambia el nombre" />
```

Y veremos como cambia inmediatamente, y el valor lo tenemos dentro del estado `nombre`.

Lo interesante, es que no es solamente que se refleje por pantalla el cambio, sino que lo tenemos guardado en el modelo de datos. Es decir,
podemos tener otro botón con una función que ejecute un `console.log()` que nos diga el valor del estado actual:

```jsx
<input type="text" onChange={e => cambiarNombre(e.target.value)} placeholder="Cambia el nombre" />

<button onClick={e => {
  console.log("El valor guardado en tu estado es: ", nombre);
}}>Mostrar valor de estado</button>
```

Entonces, nos vamos a **Inspeccionar**, **Consola**, rellenamos el `<input>`, y si le damos a `Mostrar valor de estado`, veremos por consola el valor del estado.

## Cambiar color del texto

Cambiaremos el color del texto del nombre cuando el nombre tenga cierta longitud.

Pondremos el `nombre` dentro de un `<strong>` y pornele una clase, pero en React/JSX, poner `class` nos dará un error, se ponen usando
`className`, y se la pondremos en función de una condición.

Para ello usaremos las llaves `{}` para interpolar y hacer una condición con ternarias:

```jsx
<p>Mi nombre es: <strong className={nombre.length >= 4 ? 'verde' : 'rojo'}>{nombre}</strong></p>
```

Definimos las clases en el `App.css` o en el `index.css`, en este caso, lo haremos en el `App.css`:

```css
.rojo {
  background-color: red;
}

.verde {
  background-color: green;
}
```

Visualmente veremos los cambios, si el nombre es menor a 4, pone la clase `rojo`, y si es mayor o igual, pone la clase `verde`.

Veremos la reactividad que esto tienen, y de manera reactiva e instantánea podemos cambiar tanto la estética como cualquier cosa que
vayamos a mostrar por pantalla, incluso interactuando con el modelo de datos.