# Resolviendo el ejercicio - Parte 1

## 1. Crear un componente

Creamos un nuevo archivo dentro de `components/` llamado `EjercicioComponent.js`.

Ahora definimos el componente con `rafc`:

```jsx
import React from 'react'

export const EjercicioComponent = () => {
  return (
    <div>EjercicioComponent</div>
  )
}
```

Todo va a ir dentro de un `<div>`:

```jsx
import React from 'react'

export const EjercicioComponent = () => {
  return (
    <div>
        <h2>Ejercicio con Eventos y UseState</h2>
    </div>
  )
}
```

Primer paso, hecho.

## 2. Recibir una prop con el año actual

Para recibir una `prop`, tendremos que utilizar este componente en algún sitio. Lo usaremos en el `App.js`, que es el componente principal.

Llamamos al componente:

```jsx
import { EjercicioComponent } from './components/EjercicioComponent';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <h1>El estado en React - Hook useState</h1>

        <MiPrimerEstado />

        <EjercicioComponent />
      </header>
    </div>
  );
}
```

Para recibir una `prop` con el año actual, podemos pasarlo de manera fija:

```jsx
<EjercicioComponent year="2024" />
```

Y luego, recibir esta `prop` en el componente de forma desestructurada y mostrarla por pantalla:

```jsx
export const EjercicioComponent = ({year}) => {
  return (
    <div>
        <h2>Ejercicio con Eventos y UseState</h2>
        <strong className='label'>
            {year}
        </strong>
    </div>
  )
}
```

Le cambiaremos los estilos a `label`:

```jsx
export const EjercicioComponent = ({year}) => {
  return (
    <div>
        <h2>Ejercicio con Eventos y UseState</h2>
        <strong className='label label-green'>
            {year}
        </strong>
    </div>
  )
}
```

Crearemos una segunda regla CSS llamada `label-green`:

```css
.label-green {
  background-color: green;
  color: white;
}
```

Punto dos, hecho.

## 3. Usar funciones para sacar el año

Para esto, usaremos el objeto `Date`. Dentro de nuestro componente `App`, definiremos una constante de tipo `Date` y otra donde sacaremos el
año:

```jsx
function App() {
  const fecha = new Date();
  const yearActual = fecha.getFullYear();
}
```

Con este método, sacamos el año actual.

Para pasarselo a nuestra `prop`, utilizamos las llaves `{}` e interpolamos la variable:

```jsx
function App() {
  const fecha = new Date();
  const yearActual = fecha.getFullYear();

  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <h1>El estado en React - Hook useState</h1>

        <MiPrimerEstado />

        <EjercicioComponent year={yearActual} />
      </header>
    </div>
  );
}
```

Y nos aparecerá el año en el que estamos. Y esto lo sacamos dinámicamente mediante el objeto `Date`.

Punto tres, hecho.

## 4. Usar estados y eventos para tener dos botones

* Pasar al proximo año
* Ir al año anterior
* Mostrar en todo momento el año por pantalla (**esta parte ya está hecha**)

### Pasar al proximo año

Nos crearemos dos botones dentro de un párrafo, con un espaciado con HTML:

```jsx
export const EjercicioComponent = ({year}) => {
  return (
    <div>
        <h2>Ejercicio con Eventos y UseState</h2>
        <strong className='label label-green'>
            {year}
        </strong>
        <p>
          <button>SIGUIENTE</button>
          &nbsp;
          <button>ANTERIOR</button>
        </p>
    </div>
  )
}
```

Para pasar al año anterior y volver al siguiente, lo que haremos es crearnos primero un estado, para poder conseguir el año.

Usaremos el `useState`, lo importamos, y nos creamos una constante para poder sacar el año y que se pueda modificar en todo momento. Porque se lo
estamos pasando como `prop`, pero luego cuando lo imprimimos, no va a ser una propiedad que podamos estar manipulando y que se vaya cambiando
dinámicamente y reactivamente.

Entonces, para cambiar el año, nos crearemos la contante con los dos datos del `useState`. Y vamos a imprimir `yearNow`, que va a ser la
propiedad o el estado que nos va a permitir ir modificando automáticamente ese valor:

```jsx
export const EjercicioComponent = ({year}) => {
  const [yearNow, setYearNow] = useState(year);
  
  return (
    <div>
        <h2>Ejercicio con Eventos y UseState</h2>
        <strong className='label label-green'>
            {yearNow}
        </strong>
        <p>
          <button>SIGUIENTE</button>
          &nbsp;
          <button>ANTERIOR</button>
        </p>
    </div>
  )
}
```

Crearemos las funciones para pasar al siguiente año y al anterior. Haremos uso de la función `setYearNow` para asignarle un valor al estado:

```jsx
const siguiente = e => {
  setYearNow(yearNow+1);
}

const anterior = e => {
  let operacion = yearNow - 1;
  setYearNow(operacion);
}
```

Para utilizar estas funciones como evento en los botones, usaremos el evento `onClick`, y no le tenemos que pasar ningún parámetro:

```jsx
return (
  <div>
      <h2>Ejercicio con Eventos y UseState</h2>
      <strong className='label label-green'>
          {yearNow}
      </strong>
      <p>
        <button onClick={siguiente}>SIGUIENTE</button>
        &nbsp;
        <button onClick={anterior}>ANTERIOR</button>
      </p>
  </div>
)
```

Esto funciona porque hemos usado los estados de React.

Punto cuatro, hecho.