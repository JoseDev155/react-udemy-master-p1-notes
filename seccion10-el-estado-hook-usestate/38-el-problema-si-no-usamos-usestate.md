# 38. El problema SI NO usamos useState

## ¿Qué es un **Hook**?

Básicamente es una función que nos va a permitir enganchar el estado de React y trabajar con el ciclo de vida de los componentes. En otras
palabras, es una función que cuando pasa algo, hace algo.

Y esto por defecto viene en React y es una nueva API o forma de trabajar con React que nos permite precisamente eso.
Es decir, montar/desmonatar componentes, trabajar con el estado, y que ese estado, mientras que se va modificando, se vaya reflejando en la
página. Trabajar con otros hooks que nos permiten que cuando suceda algo o se modifique cierta propiedad, se lance x función.

Vamos a empezar con el primer hook que es el del estado.

## Modificaciones en el proyecto

En el `App.js`, quitamos el párrafo y el enlace, y ponemos un `<h1>`:

```jsx
function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <h1>El estado en React - Hook useState</h1>
      </header>
    </div>
  );
}
```

Vamos a modificar los estilos que tenemos en `App.css`, modificamos la clase `.App-logo` y le ponemos un `margin-top` negativo, para tener más
espacio en la página:

```css
.App-logo {
  height: 20vmin;
  pointer-events: none;
  margin-top: -350px;
}
```

## Creando carpeta de componentes y un nuevo componente

En `src/`, creamos una carpeta en la cual vamos a estar creando los componentes, con un orden. La carpeta se llamará `components/`.

Y dentro, creamos un nuevo archivo. Nuestro componente para empezar a hacer pruebas se va a llamar `MiPrimerEstado.js`.

Y aquí vamos a crear y definir el componente utilizando el snippet `rafc`, que nos creará la estructura base de nuestro componente:

```jsx
import React from 'react'

export const MiPrimerEstado = () => {
  return (
    <div>MiPrimerEstado</div>
  )
}
```

Este componente lo vamos a utilizar en el componente principal `App.js`:

```jsx
import { MiPrimerEstado } from './components/MiPrimerEstado';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <h1>El estado en React - Hook useState</h1>

        <MiPrimerEstado />
      </header>
    </div>
  );
}
```

Se hace el `import` automáticamente utilizando la ruta correcta. Y veremos por pantalla mnuestro componente correctamente renderizado.

Ahora, todo lo que vayamos a hacer en nuestro componente, lo vamos a hacer dentro de un `<div>`:

```jsx
export const MiPrimerEstado = () => {
  return (
    <div>
        <h3>Componente: MiPrimerEstado</h3>
    </div>
  )
}
```

Para entender cómo funciona esto, tenemos aquí una propiedad o una variable `nombre` y por defecto tenemos un nombre. Imprimimos esta propiedad en una etiqueta `<strong>` con las llaves `{}`:

```jsx
export const MiPrimerEstado = () => {
    let nombre = "Víctor Robles";

  return (
    <div>
        <h3>Componente: MiPrimerEstado</h3>
        <strong>
            {nombre}
        </strong>
    </div>
  )
}
```

Lo veremos reflejado en la pantalla.

Pero si también ponemos un botón (con el texto **Cambiar**), y además, le vinculamos un evento `onClick` y llamamos a una función que se llame
`cambiarNombre`. Entonces definimos la función:

```jsx
export const MiPrimerEstado = () => {
    let nombre = "Víctor Robles";

    const cambiarNombre = e => {
        nombre = "Paquito Fernandez";
    };

  return (
    <div>
        <h3>Componente: MiPrimerEstado</h3>
        <strong>
            {nombre}
        </strong>
        &nbsp;
        <button onClick={ cambiarNombre }>Cambiar</button>
    </div>
  )
}
```

* **&nbsp;**: Sirve para que se vea una pequeña separación entre los elementos.


Si le damos clic al botón, esperaríamos que se cambiara el nombre. Pero no pasa nada. Tampoco va aparecer nada en la consola.

**¿Qué es lo que está pasando?** La lógica si trabajamos con otros frameworks, es que si debería funcionar.

Para esto viene y sirve el hook **useState**, para precisamente está funcionalidad y esta problemática poder solucionarla.

Ya hemos visto el problema, en la siguiente clase veremos cómo solucionarlo con el hook **useState**.