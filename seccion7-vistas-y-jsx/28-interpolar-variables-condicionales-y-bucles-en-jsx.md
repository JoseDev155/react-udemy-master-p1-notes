# 28. Interpolar variables, condicionales y bucles en JSX

## Creando un segundo componente

Crearemos un archivo llamado `SegundoComponente.js`. Y dentro de el usaremos un atajo/**snippet** que es el `rafc`. Si le damos **Enter** (ya
que hemos instalado la extensión previamente) nos generará la estructura básica de un componente de React:

```jsx
import React from 'react'

export const SegundoComponente = () => {
  return (
    <div>SegundoComponente</div>
  )
}
```

Ahora ya podemos usarlo dentro del `App.js`:

```jsx
import logo from './logo.svg';
import './App.css';
import MiComponente from './MiComponente';
import { SegundoComponente } from './SegundoComponente';

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
        <SegundoComponente />
      </header>
    </div>
  );
}
```

Al escribir la etiqueta automáticamente React hace el `import` de ese componente.

## Ejemplo de práctica

Crearemos un listado de libros y los imprimiremos en una lista. Borramos el contendo del `<div>` y le agregamos una
`className='segundo-componente'` para tener claro que es `SegundoComponente`. Y creamos el listado de libros accediendo a los
índices:

```jsx
export const SegundoComponente = () => {
    const libros = ["Harry Potter", "Juego de Tronos", "Clean Code"];
    
    return (
        <div className='segundo-componente'>
          <h1>Listado de libros</h1>
          <ul>
              <li>{libros[0]}</li>
              <li>{libros[1]}</li>
              <li>{libros[2]}</li>
          </ul>
        </div>
    )
}
```

Y pondremos un `<hr />` entre los componentes en el `App.js`. Y para que se visualice correctamente el `<hr />`, los meteremos dentro de un
`<div>` con un `className='componentes'`:

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
        <div className='componentes'>
          <hr />
          <SegundoComponente />
          <hr />
          <MiComponente />
        </div>
      </header>
    </div>
  );
}
```

Y quitamos el `<hr />` del componente `MiComponente.js`:

```jsx
const MiComponente = () => {
  let nombre = "Víctor";
  let web = "victorroblesweb.es";

  let usuario = {
      nombre: "Víctor",
      apellidos: "Robles",
      web: "victorroblesweb.es"
  };

  console.log(usuario);

  return (
      <div className="mi-componente">
        <h2>Componente creado</h2>
        <h3>Datos del usuario:</h3>
        <ul>
          <li>Nombre: <strong>{usuario.nombre}</strong></li>
          <li>Apellidos: <strong>{usuario.apellidos}</strong></li>
          <li>Web: <strong>{usuario.web}</strong></li>
        </ul>
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

## Bucles

Para recorrer los elementos de un array de forma óptima usaremos las llaves `{}` para hacer instrucciones de JavaScript. en este caso,
usaremos `forEach()`:

```jsx
export const SegundoComponente = () => {
    const libros = ["Harry Potter", "Juego de Tronos", "Clean Code"];
    
    return (
        <div className='segundo-componente'>
            <h1>Listado de libros</h1>
            <ul>
                {
                    libros.forEach(libro => {
                        return <li>{libro}</li>;
                    })
                }
            </ul>
        </div>
    )
}
```

Esto nos dará un error ya que no mostrará los libros, pero si usamos el `map()` si que lo hará:

```jsx
export const SegundoComponente = () => {
    const libros = ["Harry Potter", "Juego de Tronos", "Clean Code"];
    
    return (
        <div className='segundo-componente'>
            <h1>Listado de libros</h1>
            <ul>
                {
                    libros.map(libro => {
                        return <li>{libro}</li>;
                    })
                }
            </ul>
        </div>
    )
}
```

Esto es porque en JSX, para recorrer y mostrar un elemento, necesitamos tener acceso a los índices. Por eso es más recomendable utilizar `map()`
en React. Para acceder a los índices de los elementos de forma más sencilla.

Ahora, aparentemente no veremos ningún error, pero si inspeccionamos en la consola del navegador, veremos el siguiente error:
`Each child in a list should have a unique "key" prop`. Porque le tenemos que indicar un índice para poder acceder luego a ese elemento
fácilmente y poder modificarlo, o lo que sea. Tenemos que hacer que cada elemento sea único o tenga un identificador único.

Para eso, aplicaremos una `key` y le indicaremos el índice de cada elemento:

```jsx
export const SegundoComponente = () => {
    const libros = ["Harry Potter", "Juego de Tronos", "Clean Code"];
    
    return (
        <div className='segundo-componente'>
            <h1>Listado de libros</h1>
            <ul>
                {
                    libros.map((libro, indice) => {
                        return <li key={indice}>{libro}</li>;
                    })
                }
            </ul>
        </div>
    )
}
```

Esta es la forma en que funciona React. Y se sigue mostrando todo igual pero sin el mensaje de error en la consola del navegador.

## Condicionales

Si quitamos el contenido del arrary `libros` y lo dejamos vacio, no se va a mostrar nada en el listado. Entonces, queremos  ue se ejecute el
bucle y se nos muestren cada uno de los elementos, en el caso de que haya algo dentro del array, pero si no hay nada, que se muestre un
mensaje de "**No hay ningún libro disponible**".

Al igual que con los bucles, esto lo podemos hacer utilizando las llaves `{}` antes de renderizar la lista:

```jsx
export const SegundoComponente = () => {
    // const libros = ["Harry Potter", "Juego de Tronos", "Clean Code"];
    const libros = [];
    
    return (
        <div className='segundo-componente'>
            <h1>Listado de libros</h1>
            {libros.length >= 1 ?
                <ul>
                    {
                        libros.map((libro, indice) => {
                            return <li key={indice}>{libro}</li>;
                        })
                    }
                </ul>
            :
                <p>No hay libros</p>
            }
        </div>
    )
}
```

Esto nos mostrará errores, porque este `if` o **ternaria** no va a entender que trozos de código tiene que interpretar cuando se cumpla la
condición o no. Sobre todo, cuando es algo multilínea o un condicional, y lo que vamos a estar devolviendo cuando se hace bien la condición es
algo multilínea.

Para eso, debemos meter entre paréntesis `()` lo que queremos que entre dentro de la condición al igual que el resultado, para que JSX no se
confunda. Así haremos lo que queremos que se renderice de manera condicional:

```jsx
export const SegundoComponente = () => {
    // const libros = ["Harry Potter", "Juego de Tronos", "Clean Code"];
    const libros = [];
    
    return (
        <div className='segundo-componente'>
            <h1>Listado de libros</h1>
            {libros.length >= 1 ?
                (<ul>
                    {
                        libros.map((libro, indice) => {
                            return <li key={indice}>{libro}</li>;
                        })
                    }
                </ul>)
                : (<p>No hay libros</p>)
            }
        </div>
    )
}
```

Así si funcionaría. En el navegador veremos que dice **No hay libros**. Pero si tuviéramos el array con contenido:

```jsx
export const SegundoComponente = () => {
    const libros = ["Harry Potter", "Juego de Tronos", "Clean Code"];
    // const libros = [];
}
```

Nos mostraría el listado de libros. En el caso que quitemos quitemos los paréntesis al `else`:

```jsx
export const SegundoComponente = () => {
    // const libros = ["Harry Potter", "Juego de Tronos", "Clean Code"];
    const libros = [];
    
    return (
        <div className='segundo-componente'>
            <h1>Listado de libros</h1>
            {libros.length >= 1 ?
                (<ul>
                    {
                        libros.map((libro, indice) => {
                            return <li key={indice}>{libro}</li>;
                        })
                    }
                </ul>)
                : <p>No hay libros</p>
            }
        </div>
    )
}
```

Va a funcionar igual, porque es solamente una línea. Pero cuando son muchas líneas, JSX se va a confundir, por eso tenemos que poner los
paréntesis.