# 39. Como usar el Hook useState de React

Para poder manejar un estado, tenemos que utilizar el hook **useSate**.

## Importando useState

Lo importamos con las llaves `{}` y el nombre del hook:

```jsx
import React, { useState } from 'react'
```

Todo lo que tenga `use` delante es un hook.

## Funcionamiento de useState

Esto que estamos haciendo:

```jsx
let nombre = "Víctor Robles";

const cambiarNombre = e => {
    nombre = "Paquito Fernandez";
};
```

Esta sería la problemática que no funciona y nos gustaría que funcionara, podemos hacer que funcione precisamente utilizando un estado.

Con un **useState** lo podemos hacer muy fácil, nos creamos una constante y este hook se caracteriza porque va a tener 2 partes:

* Por la variable que va a guardar ese dato del estado
* Por la función que va a permitirnos acceder a ese estado y modificarlo

Para eso usaremos la desestructuración utilizando los corchetes `[]`, y nos definimos un estado que sea `nombre`, y su función, uqe va a
permitirnos acceder al `nombre` y asignarle un valor va a ser `setNombre`.
Todas las funciones de un estado normalmente se llaman `set` y el nombre de la variable o el nombre del dato que vamos a querer modificar. Aunque
no es obligatorio, es una convención.

Ahora ya podemos utilizar la función del estado `useState()`. Es una función simplemente que va a recibir un parámetro, siempre va a recibir o
vamos a tratar de hacer que tenga un parámetro. En este caso, el parámetro por defecto será el que teniamos en el ejemplo anterior:

```jsx
const [ nombre, setNombre ] = useState("Víctor Robles");
```

Entonces, ya tenemos el dato del `nombre`. Esto esta funcionando igual que antes. Aunque nos va a mostrar un error si le damos clic al botón.

El `nombre` es una variable porque estamos accediendo a ella mediante una desestructuración que hemos hecho, y tenemos la función `setNombre`.

Y esto, automáticamente es lo que nos está devolviendo el `useState`, porque nos devuelve un array. Y si queremos trabajr con el de forma
sencilla, tenemos que desestructurarlo.

Quitamos los eventos del botón para que no nos de errores (por ahora):

```jsx
import React, { useState } from 'react'

export const MiPrimerEstado = () => {
    /*
    // Problematica
    let nombre = "Víctor Robles";

    const cambiarNombre = e => {
        nombre = "Paquito Fernandez";
    };
    */

    const [ nombre, setNombre ] = useState("Víctor Robles");

  return (
    <div>
        <h3>Componente: MiPrimerEstado</h3>
        <strong>
            {nombre}
        </strong>
        &nbsp;
        <button>Cambiar</button>
    </div>
  )
}
```

Si cambiamos el valor aquí:

```jsx
const [ nombre, setNombre ] = useState("Fran");
```

Se mostrará **Fran** por pantalla, porque ese valor que ponemos aquí, es el que se está asignando a la variable `nombre`. Pero de momento, lo
dejaremos como estaba:

```jsx
const [ nombre, setNombre ] = useState("Víctor Robles");
```

Si quisieramos hacer lo que hemos hecho de asignarle un evento `onClick` al botón y modificar el `nombre`, lo podemos hacer. Porque podemos crear
ahora una función, `cambiarNombre`. Y la definimos por aquí de la misma manera que hicimos antes:

```jsx
export const MiPrimerEstado = () => {
    /*
    // Problematica
    let nombre = "Víctor Robles";

    const cambiarNombre = e => {
        nombre = "Paquito Fernandez";
    };
    */

    const [ nombre, setNombre ] = useState("Víctor Robles");

    const cambiarNombre = e => {
      nombre = "Fran";
    }

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

Cuando demos clic, le asignamos ese nombre. Pero no va a funcionar, porque `nombre` es una constante. Aunque cambiemos la declaración:

```jsx
let [ nombre, setNombre ] = useState("Víctor Robles");
```

Si le damos clic al botón, no nos mostrará ese aviso, pero no va a funcionar.

Para signarle un valor a un estado, al estado `nombre`, utilizamos `setSate`, en nuestro caso, es `setNombre`. Y como parámetro, le pasamos
el dato que queremos asignarle a la variable o estado `nombre`. Lo hacemos de la siguiente manera:

```jsx
export const MiPrimerEstado = () => {
    /*
    // Problematica
    let nombre = "Víctor Robles";

    const cambiarNombre = e => {
        nombre = "Paquito Fernandez";
    };
    */

    const [ nombre, setNombre ] = useState("Víctor Robles");

    const cambiarNombre = e => {
      setNombre("Francisco");
    }

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

Y eso es todo, no hace falta indicar nada más.

Ahora, si le damos clic al botón, se cambia automáticamente el `nombre`.

Y si nos vamos al **Inspector** de elementos del navegador y localizamos el `<div>` y el `nombre`, tenemos el nombre por defecto. Pero si le damos
clic al botón, veremos que solo se iluman la etiqueta `<strong>` donde estamos imprimiendo el `nombre`.

Porque React se encarga de, precisamente al ser reactivo y con el uso de los estados, se encarga de no actualizar toda la pantalla, sino
actualizar solamente la parte que necesita. Y en este caso, evidentemente necesita modificar el `nombre`, y solamente modifica eso
porque el Estado nos permite hacer eso.