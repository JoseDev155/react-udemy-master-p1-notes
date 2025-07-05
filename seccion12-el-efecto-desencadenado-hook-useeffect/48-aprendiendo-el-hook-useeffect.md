# 48. Aprendiendo el hook useEffect

## Creando componente nuevo

Creamos un nuevo componente dentro de `components/` que se llamará `PruebasComponent.js`.

Usamos el snippet `rafc` para que nos cree la función inical del componente:

```jsx
import React from 'react'

export const PruebasComponent = () => {
  return (
    <div>PruebasComponent</div>
  )
}
```

Le agregamos un `<h1>`:

```jsx
import React from 'react'

export const PruebasComponent = () => {
  return (
    <div>
        <h1>El efecto - Hook useEffect</h1>
    </div>
  )
}
```

## Cargando componente en el `App.js`

Lo cargamos en el `App.js` y también quitamos el párrafo y el enlace:

```jsx
import logo from './logo.svg';
import './App.css';
import { PruebasComponent } from './components/PruebasComponent';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <PruebasComponent />
      </header>
    </div>
  );
}
```

## Cambios en el CSS

En el `App.css`, modificamos las clases `.App-logo` y en el `.App-header`, nos deben quedar así:

```css
.App-logo {
  height: 10vmin;
  pointer-events: none;
}

.App-header {
  background-color: #282c34;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  font-size: calc(10px + 2vmin);
  color: white;
}
```

Para que se alinee un poco arriba.

## Preparando la practica de useEffect

Si tenemos un estado, creando una constante y usando la desestructuración, le asignamos unos valores por defecto:

```jsx
import React, { useState } from 'react'

export const PruebasComponent = () => {
    const [usuario, setUsuario] = useState("Víctor Robles");

  return (
    <div>
        <h1>El efecto - Hook useEffect</h1>
    </div>
  )
}
```

Luego, podemos modificar ese estado cada vez que queramos. Podemos tener un campo de formulario, un `<input>` de tipo texo y va a tener un evento
`onChange`, que cuando modifiquemos lo que sea, se va a ejecutar la función `modUsuario()`. También le pondremos un `placeholder`.

También vamos a imprimir en un `<strong>` el `usuario`:

```jsx
export const PruebasComponent = () => {
    const [usuario, setUsuario] = useState("Víctor Robles");

  return (
    <div>
        <h1>El efecto - Hook useEffect</h1>
        <strong>{usuario}</strong>
        <input type="text" 
               onChange={ modUsuario } 
               placeholder="Cambia el nombre" 
            />
    </div>
  )
}
```

Definimos la función con una constante y recogiendo el evento vinculado a ese campo de texto. Y meteremos el `<input>` en una etiqueta `<form>`,
que ya tiene un display distinto:

```jsx
export const PruebasComponent = () => {
    const [usuario, setUsuario] = useState("Víctor Robles");

    const modUsuario = e => {
        setUsuario(e.target.value);
    };

  return (
    <div>
        <h1>El efecto - Hook useEffect</h1>
        <strong>{usuario}</strong>
        <form>
            <input type="text" 
                   onChange={ modUsuario } 
                   placeholder="Cambia el nombre" 
                />
        </form>
    </div>
  )
}
```

Si queremos cambiar el nombre, funciona correcamente.

Le pondremos un `className` diferente al `<strong>` y le vamos a poner lo que hicimos en el proyecto anterior, del `label`:

```jsx
<strong className='label'>{usuario}<strong>
```

Y copiamos el estilo del proyecto anterior, del `App.css`. Y lo pegamos en el `App.css` de nuestro proyecto actual. Le agreamos también un
`margin: 15px`, y un `display: block` para que no haga caso a los márgenes:

```css
.label {
  display: block;
  background-color: lightblue;
  border-radius: 5px;
  padding: 5px;
  color: #444;
  margin: 15px;
}

.label-green {
  background-color: green;
  color: white;
}
```

## Explicación de qué es el hook useEffect

Si queremos lanzar una funcionalidad, lanzar un efecto o que se genere un efecto desencadenado cuando hacemos algún cambio en el estado de
nuestro componente. Es decir, se modifique lo que se modifique en nuestro componente.

Si tenemos muchos estados, y queremos que nada más cargar el componente se ejecute una función, y además, que nada más se produzca un cambio en
el componente, en cualquiera de los estados, lance un efecto desencadenado, se ejecute una función o algo así.

Para hacer esto, cada vez que hagamos un cambio, como cada vez vamos a estar tocando, vamos a hacer un `onChange`, podemos hacer un:

```jsx
const modUsuario = e => {
    setUsuario(e.target.value);

    console.log("Ha habido un cambio en usuario");
};
```

Pero esto solo afectaría cuando toquemos el `<input>` y realmente no es algo global. Si nos vamos a la consola del navegador, se va a estar
ejecutando tantas veces como hagamos cambios.

Pero no es un efecto desencadenado ante cualquier cambio de cualquier estado. De hecho, no es algo automático. Lo tenemos que ejecutar en la
función.

Queremos algo que se ejecute nada más cargar nuestro componente, nada más cargar nuestro componente que se ejecute un método.

Para hacer esto lo haremos con `useEffect`.

## Uso de useEffect

Si escribimos `useEffect`, automáticamente se nos hace el `import`:

```jsx
import React, { useEffect, useState } from 'react'
```

Es importante tener bien los `import`'s de los hooks que vayamos usando.

Vamos a usar la función `useEffect`, básicamente lo que tiene cómo parámetro es otra función, una función de **callback**, anónima, y va a
ser la funcionalidad que se va a ejecutar. Podemos hacer un:

```jsx
useEffect(() => {
  console.log("Has cargado el componente PruebasComponent !!");
});
```

Esto se va a ejecutar cada vez que carguemos el componente y cada vez que se produzca un cambio en nuestro componente.

Nada más cargar la aplicación, lo primero que se ejecuta es el `useEffect`, se ejecuta automáticamente. Además, si hacemos algún cambio
en el formulario, se está ejecutando todas las veces que se produce un cambio en esta propiedad.

Además, si tuvieramos otro `<input>` o un `<button>`, que hiciera un cambio en la propiedad que tenemos o en otra cualquiera.
Podemos tener otra propiedad que sea `fecha`, y en el `onClick`, modificamos esa fecha llamando una función `cambiarFecha()`, la definimos
también.

Haremos que le aplicque a `fecha`, usando el objeto `Date` y utilizamos el método `toLocaleDateString`, para asignarle la fecha actual. Cuando le
demos clic, se va a cambiar la fecha.

Y para que no se ejecute el formulario, lo meteremos dentro de un párrafo para luego solventar esos problemas con el formulario:

```jsx
export const PruebasComponent = () => {
    const [usuario, setUsuario] = useState("Víctor Robles");
    const [fecha, setFecha] = useState("01-01-1998");

    const modUsuario = e => {
        setUsuario(e.target.value);
    };

    const cambiarFecha = e => {
      setFecha(new Date().toLocaleDateString());
    }

    useEffect(() => {
      console.log("Has cargado el componente PruebasComponent !!");
    });

  return (
    <div>
        <h1>El efecto - Hook useEffect</h1>
        <strong className='label'>{usuario}</strong>
        <p>
            <input type="text" 
                   onChange={ modUsuario } 
                   placeholder="Cambia el nombre" 
            />

            <button onClick={cambiarFecha}>Cambiar fecha</button>
        </p>
    </div>
  )
}
```

Si le damos a **Cambiar fecha**, hay un cambio en el componente. Pero la `fecha` que estamos cambiando siempre es la misma y tampoco la estamos
imprimiendo por pantalla.

La vamos a imprimir:

```jsx
<strong>{fecha}</strong>
```

Veremos la fecha. Si le damos a **Cambiar fecha**, la cambia a la actual. También podríamos ponerle la hora, para notar ese cambio.

Incluso, para ver realmente el cambio, podemos utilizar el `Date.now()`:

```jsx
const cambiarFecha = e => {
    setFecha(Date.now());
}
```

Si le damos a **Cambiar fecha**, nos pone la fecha en formato **Unix**, en formato **Time**, es decir, esto siempre va a estar cambiando.

Si nos damos cuenta, el `useEffect` siempre se va a lanzar hayamos cargado el componente o realizado un cambio en un estado:

```jsx
useEffect(() => {
    console.log("Has cargado el componente PruebasComponent o has realizado un cambio en un estado!!");
});
```

Si modificamos el `nombre`, tantas veces como estemos modificando el `nombre` se va a estar ejecutando el `useEffect`, se está ejecutando ese
efecto desencadenado.

Ahora mismo esto no puede parecer útil, pero luego puede servir porque cuando hagamos una modificación en alguna propiedad de la aplicación o
estado de la aplicación, queremos que se refleje en la interfaz. O se actualiza algo por **AJAX**, queremos que se actualice también la
interfaz. O si queremos detectar algo, o cada vez que se cargue un componente, el `useEffect` sirve para eso.

Si le damos a **Cambiar fecha**, automáticamente nos muestra el mensaje por la consola del navegador.

Ahora, a lo mejor no queremos que se ejecute cada vez que realizamos un cambio, simplemente queremos que se lanze una vez nada más cargamos el
componente, que es algo muy común. Es decir, cargamos el componente, sacamos un listado, luego hay una modificación en ese listado, pues queremos que se actualice, pero ya lo podemos lanzar de otra manera.

Entonces, si queremos que solamente se ejecute una vez, cuando carguemos nuestro componente le tenemos que poner un segundo parámetro e indicarle
cuando queremos que se ejecute, le ponemos los corchetes `[]` y si lo dejamos vacío, este `useEffect` solo se ejecuta una vez:

```jsx
useEffect(() => {
    console.log("Has cargado el componente PruebasComponent!!");
}, []);
```

Es decir, nada más cargar la aplicación, solo al cargar el componente. Entonce, lo de **has realizado un cambio en un estado** no nos sirve,
porque solo se va a ejecutar una vez.

Si actualizamos la pantalla, nos saldrá el mensaje por la consola del navegador. Si hacemos un cambio, ya no se ejecuta el `useEffect`. Si
cambiamos la `fecha` tampoco se ejecuta de nuevo el `useEffect`.

Pero podemos crearnos un segundo `useEffect`, muy parecido al que tenemos, que haga otra cosa. Que se ejecute solo si cambiamos el
`usuario`.

Para indicar eso tenemos que pasarle en los corchetes `[]` en qué propiedades queremos que esto se dispare este efecto. Queremos que se
dispare en `usuario`:

```jsx
useEffect(() => {
    console.log("Has modificado el usuario !!");
}, [usuario]);
```

Cuando cambiemos la propiedad o estado `usuario`, queremos que se ejecute esto.

Si actualizamos la pantalla, nos dice **Has modificado el usuario !!** porque la primera vez obviamente siempre se va a lanzar, pero si lo
modificamos ahora se ejecuta tantas veces como modifiquemos el `usuario`.

Sin embargo, si cambiamos la `fecha`, no se va a lanzar absolutamente nada. Así que ya hemos visto para qué sirve a grandes rasgos `useEffect`.