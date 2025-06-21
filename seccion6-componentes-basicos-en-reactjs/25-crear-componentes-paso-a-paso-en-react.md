# 25. Crear componentes paso a paso en React

## Modificando nuestro proyecto `01-primeros-pasos`

Eliminar archivos:

* `setupTests.js`
* `reportWebVitals.js`
* `App.test.js`

Quitamos la referencia `reportWebVitals.js` del `index.js` y el **Modo Estricto** de React:

```jsx
import reportWebVitals from './reportWebVitals';

root.render(
    <React.StrictMode></React.StrictMode>
);
reportWebVitals();
```

Y el `index.js` nos quedará de la siguiente manera:

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

Luego de eliminar estos archivos, no nos da ningún problema.

## Cambios en `App.js`

Vamos a hacer cambios en la template que se está renderizando por pantalla. Quitaremos el enlace `<a></a>` y nos quedaría así:

```jsx
function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Bienvenido al master en react!!
        </p>
      </header>
    </div>
  );
}
```

## Crear un componente

Vamos a aprender a crear un componente, cargar dentro de otro componente o donde queramos, dentro de una aplicación de React.

### Forma básica

Creando un nuevo archivo llamado `MiComponente.js`. Lo normal es que los componentes empiecen en mayúscula, y apartir de ahí utilicen **Camel Case**.

¿Qué partes tiene un componente? Ejemplo:

```jsx
// Importar modulos de react / dependencias
import React from "react";

// Función del componente
const MiComponente = () => {
    return <p>Este es mi primer componente</p>;
};

// Export
export default MiComponente;
```

Importamos `react`, que es el paquete principal que tenemos en el `node_modules/`.

Creamos la función del componente con el mismo nombre del archivo. Usamos una función flecha ya que es la forma actual de utilizarlo.
Pero podríamos usar `function` sin ningún problema:

```jsx
function MiComponente() {
}
```

Dentro del componente debemos tener un `return`, que devuelve el HTML que queremos mostrar por pantalla. No sería típico tener un párrafo y
devolver simplemente un texto o un poco de HTML:

```jsx
return <p>Este es mi primer componente</p>;
```

Ya veremos si esto funciona.

Y por último, lo exportamos, por `default` porque solo vamos a devolver por defecto una función y devolvemos el componente. Ahora, ya podemos
utilizar el componente en otros componentes.

## Cargar `MiComponente` en el componente `App`

Lo importamos. Si no le pusieramos el `default`, tendríamos que utilizar las llaves `{}` para seleccionar en concreto la función que queremos.
Pero lo normal es que cada fichero sea un componente, y no tener varios componentes en un mismo fichero. No sería una buena práctica.

Ahora, cargamos nuestro componente, utilizando su etiqueta:

```jsx
import logo from './logo.svg';
import './App.css';
import MiComponente from './MiComponente';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Bienvenido al master en react!!
        </p>
      </header>

      {/* Cargar mi primer componente */}
      <MiComponente />
    </div>
  );
}

export default App;
```

Podemos utilizar las llaves `{}` para hacer comentarios en React. Nos permiten incluir JavaScript, para hacer bucles, condiciones y comentarios
de JavaScript.

Como la etiqueta no tendrá contenido, la cerramos de esta manera `<MiComponente />`.

Esto significa que ahora, en el navegador, debería mostrarse lo que esta devolviendo el componente `MiComponente`. Aunque se muestra en las **herramientas de desarrollo**, al estar fuera del `<div>` principal, no lo estamos viendo pero esta ahí.

Para que se muestre, lo metemos dentro del `<header>`, ya que los estilos que tiene, no colorean lo que hay dentro de él:

```jsx
import logo from './logo.svg';
import './App.css';
import MiComponente from './MiComponente';

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

export default App;
```

Y ahora, si va a aparecer nuestro componente.

## Devolver múltiples etiquetas en un componente

El propio componente en sí puede incluir un `<hr />` aunque tendremos un problema, porque estamos intentando devolver 2 etiquetas a la vez:

```jsx
const MiComponente = () => {
    return (<hr /><p>Este es mi primer componente</p>);
};
```

Para devolver 2 etiquetas o más, debemos meterlas entre paréntesis `()`. Pero tendremos otro problema, no podemos poner 2 etiquetas (o por lo
menos la raíz) no puede ser 2 etiquetas o más.
Es decir, que cada componente tiene que renderizar una caja, un `<div>` o un contenedor, y dentro, tener todo el resto de etiquetas y contenido
que vaya a renderizar ese componente.

Tenemos tres formas de renderizar múltiples etiquetas y mucho contenido dentro de un componente:

* Utilizando los `<Fragment>`
* Utlizando la sintaxis abreviada de los `<Fragment>`
* Utilizando un `<div>`

O un contenedor cualquiera, puede ser `<div>`, `<main>`, `<section>`, entre otros, dentro de este `return`.