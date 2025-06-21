# 26. Renderizar muchas etiquetas en JSX

Como vimos antes, esto no noa va a funcionar:

```jsx
const MiComponente = () => {
    return (
        <hr />
        <h2>Componente creado</h2>
        <p>Este es mi primer componente</p>
        <ul>
            <li>
                React
            </li>
            <li>
                Angular
            </li>
            <li>
                Vue
            </li>
        </ul>
    );
};
```

El mismo `eslint` nos dirá: `Parsing error: Adjacent JSX elements must be wrapped in an enclosing tag. Did you want a JSX fragment <>...</>?`.
Podemos usar un `Fragment` vacio, o usar la etiqueta `<Fragment>`, un `<div>`, o una caja cualquiera.

## `Fragment` vacio

Todo el contenido que queremos que renderice el componente, lo podemos meter dentro de una etiqueta vacía:

```jsx
const MiComponente = () => {
    return (
        <>
            <hr />
            <h2>Componente creado</h2>
            <p>Este es mi primer componente</p>
            <ul>
                <li>
                    React
                </li>
                <li>
                    Angular
                </li>
                <li>
                    Vue
                </li>
            </ul>
        </>
    );
};
```

Esto ya es válido. Si nos vamos al navegador, veremos el componente por pantalla, aunque el `<hr />` no se visualiza como debería (probablemente
los estilos lo bloquean).

## Objeto `Fragment`

Requiere importar el objeto `Fragment` y usarlo así:

```jsx
import React, {Fragment} from "react";

// Función del componente
const MiComponente = () => {
    return (
        <Fragment>
            <hr />
            <h2>Componente creado</h2>
            <p>Este es mi primer componente</p>
            <ul>
                <li>
                    React
                </li>
                <li>
                    Angular
                </li>
                <li>
                    Vue
                </li>
            </ul>
        </Fragment>
    );
};
```

El resultado sería el mismo, tanto usando la sintaxis abreviada como usando la sintaxis no abreviada de los `Fragment`.

Esto lo que haría es meter dentro de la misma raíz donde estamos incrustando nuestro componente o donde lo estamos llamando, es decir,
donde estamos llamando `<MiComponente>`, todo el HTML iría al mismo nivel que el código HTML que ya teníamos antes:

```jsx
function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Bienvenido al master en react!!
        </p>

        {/* Cargar mi primer componente */}
        <MiComponente />
      </header>
    </div>
  );
}
```

Es decir, al mismo nivel que `<img>` y que el `<p>` (en el `App.js`)

## `<div>`

Usamos un `<div className="mi-componente">`, porque en el lugar de `class` usamos `className`:

```jsx
const MiComponente = () => {
    return (
        <div className="mi-componente">
            <hr />
            <h2>Componente creado</h2>
            <p>Este es mi primer componente</p>
            <ul>
                <li>
                    React
                </li>
                <li>
                    Angular
                </li>
                <li>
                    Vue
                </li>
            </ul>
        </div>
    );
};
```

Y funciona igual, aparte que ahora si se ve correctamente el `<hr />`, porque todo esta contenido dentro de un `<div>`, es decir, el `<div>`
está al mismo nivel, pero hay un subnivel que es el contenido que tiene ese `<div>`.

Con el `<div>` tenemos más control de lo que renderiza o no el componente.

## Reutilizando un componente

Podemos replicar el componente las veces que queramos:

```jsx
function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Bienvenido al master en react!!
        </p>

        {/* Cargar mi primer componente */}
        <MiComponente />
        <MiComponente />
        <MiComponente />
        <MiComponente />
      </header>
    </div>
  );
}
```

Se mostrará cuatro veces el mismo contenido.

## **Nota de la clase**

Ya no es necesario inportar explícitamente `React` desde la versión 17 de React en la creación de un componente. En React 17 y versiones
posteriores, el compilador JSX (como Babel o TypeScript) incluye automáticamente la referencia a React en el código generado

Antes (React 16 y versiones anteriores):
```jsx
import React from "react";
 
function App() {
  return <h1>Hello, World!</h1>;
}
 
export default App;
```

Ahora (React 17+):

```jsx
function App() {
  return <h1>Hello, World!</h1>;
}
 
export default App;
```