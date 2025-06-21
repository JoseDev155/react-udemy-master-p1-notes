# 24. ¿Qué es un componente en React JS?

Vamos a ver cómo funciona un componente y para ello veremos el ejemplo que viene por defecto en nuestro proyecto de React, cuando lo instalamos
por defecto.

## Definición de componente

Es una parte de la aplicación. Puede ser una clase, una función, pero se va a traducir en una parte de la aplicación, en una parte de la interfaz
de la web, o en una parte de la apliación como tal.

## Ejemplo

Si queremos hacer que una web esté basada en componentes, podemos tener un componente para cada cosa que la comforma.

Podemos tener un componente que sea la parte de la **cabecera**, que imprima el logo y todo el menú. Podemos tener otro componente para la
parte de los iconos de **redes sociales**.

Podemos tener un componente que sea un **artículo**, y que luego, al hacer un bucle, se vayan replicando los diferentes componentes de
artículo.

Podemos tener un componente que sea la **barra lateral**. Podemos tener un componente que sea el **buscador** solamente.

Cada una de estas partes de la aplicación son un componente. Y luego, en el componente principal que incluye a todos los componentes, invocamos al
**header**. Y dentro invocamos a los iconos de **redes sociales**.
Luego, creamos un `<div>` con el contenido principal.
Cremos otro `<div>` para la **barra lateral**, y dentro cargamos el componente del **buscador**, cargamos el resto de componentes de la barra
lateral.
Dentro del contenido principal, cargamos el componente de **artículo** y luego vamos recorriendo un array de objetos que traiga el resto de
artículos que también se van a leer mediante un componente.

Básicamente, es una forma de separar una página web en pequeñas partes lógicas. Pero luego, también puede ser que sea algo más grande, es decir
que sea una sección de la web.

Es decir, tener un componente para la página de inicio, un componente para la página de artículos, un componente para la página de contacto.

## Estructura de un componente en React actualmente

Vamos a tener una serie de `import`´s, donde vamos a importar tanto recursos como dependencias de React.

Luego, vamos a tener una función que va a ser el componente principalmente. Y dentro de esta función vamos a tener propiedades o
`props` que vamos a poder cargar en la parte de HTML o de **JSX** que se va a renderizar.

Porque al final, lo que se va a renderizar no es HTMl sino que es una versión de HTML mezclada con React y que podemos meter JavaScript y HTML
en el mismo código de la vista que queramos imprimir y podemos hacer cierta lógica: podemos interpolar variables, condiciones, lógica y
mezclar un poco de JavaScript con un poco de HTML, mezclar HTML con JavaScript o el JavaScript de React, y eso se traduce a lo que es
**JSX**.

Y con el `return` renderizamos el JSX (o HTML). Ejemplo de componente usando el código por defecto del `App.js`:

```jsx
import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Bienvenido al master en react!!
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

## Peculiaridades de JSX a diferencia de HTML

Hay algunas propiedades que debemos cambiarle el nombre o utilizar otra. Ejemplo: en lugar de utilizar `class`, usamos `className` para nuestras
etiquetas:


```jsx
<div className="App"></div>
```

Para imprimir usamos las llaves:

```jsx
<img src={logo} className="App-logo" alt="logo" />
```

Luego veremos como hacer condiciones, bucles, y como meter JavaScript dentro de lo que es el HTML que renderiza un componente.

Para que funcione, debemos exportarlo para poder tener disponible luego la etiqueta de ese componente:

```jsx
export default App;
```

El nombre de la etiqueta del componente depende del nombre que le pongamos a la función, y cómo la estemos exportando.

En este caso, en el `index.js` estamos usando la etiqueta de ese compoenente `App`, para cargar el primer componente de nuestra
aplicación:

```jsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
import App from './App';
import reportWebVitals from './reportWebVitals';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);

// If you want to start measuring performance in your app, pass a function
// to log results (for example: reportWebVitals(console.log))
// or send to an analytics endpoint. Learn more: https://bit.ly/CRA-vitals
reportWebVitals();
```