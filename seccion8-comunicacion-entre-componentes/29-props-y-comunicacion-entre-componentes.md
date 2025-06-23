# 29. Props y comunicación entre componentes

Crearemos un tercer componente llamado `TercerComponente.js`. Todos los componentes ahora mismo los estamos creando en la raíz de `src/`. Cuando
hagamos aplicaciones un poco más grandes, lo suyo sería tener una carpeta `components/`, y dentro, que esten todos los componentes de la
aplicación. Esos es lo recomendable.
Sino, el directorio `src/` será muy grande.

Creamos el componente utilizando el atajo `rafc`:

```jsx
import React from 'react'

export const TercerComponente = () => {
  return (
    <div>TercerComponente</div>
  )
}
```

Y luego en `App.js`, vamos a utilizar ese tercer componente en el componente que se está cargando la aplicación completa.

Recordemos que en `ìndex.js`, podemos modificar que componente va a ser el principal. En este caso, nos da igual dejarlo en `App.js` porque es el
componente cobre el cual estamos cargando más componentes:

```jsx
import logo from './logo.svg';
import './App.css';
import MiComponente from './MiComponente';
import { SegundoComponente } from './SegundoComponente';
import { TercerComponente } from './TercerComponente';

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
          <TercerComponente />
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

Sin ningún tipo de problema, lo veremos por pantalla.

Este `TercerComponente.js` tendrá dentro:

```jsx
export const TercerComponente = () => {
  return (
    <div>
        <h1>Comunicación entre componentes</h1>
    </div>
  )
}
```

## Comunicación entre componentes

Esto es simplemente pasar datos de un componente a otro componente. En React, vamos a tener multitud de componentes para contruir nuestra
aplicación web, entonces va a llegar un punto que va a ser fundamental poder pasar datos de un componente a otro.

Para esto vamos a usar las `props` de los componentes, que son propiedades que podemos pasar aquí a la función del componente para
indicar que vamos a recibir unos datos. Es decir, podemnos poner directamente `props`, y también, antes del `return`, haremos un
`console.log()` para ver qué tenemos dentro de las `props` por defecto:

```jsx
export const TercerComponente = (props) => {
    console.log(props);

    return (
        <div>
            <h1>Comunicación entre componentes</h1>
        </div>
    )
}
```

Las propiedades que lleguen por aquí, las vamos a poder utilizar y mostrar por pantalla.

Cuando se renderice `TercerComponente.js`, nos vamos a la consola del navegador, y veremos que no tenemos nada en las `props`, tenemos un objeto vacío.

Pero podemos indicarle al componente cuando lo renderizamos en el `App.js`, cuando llamamos a su etiqueta, le vamos a indicar unas propiedades:

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
          <TercerComponente nombre="Víctor" apellidos="Robles" />
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

Si nos vamos a la consola del navegador, veremos que el objeto de las `props` está siendo formado con las propiedades que le pusimos a la
etiqueta del componente.

Se va formateando, generando, un objeto. Podemos añadirla tantas `props` como queramos y pasarle tanta información como queramos, incluso un
objeto:

```jsx
function App() {
  const ficha_medica = {
    altura: "187cm",
    grupo: "H+",
    estado: "Bueno",
    alergias: "Ninguna"
  }

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
          <TercerComponente 
            nombre="Víctor" 
            apellidos="Robles" 
            ficha={ficha_medica} 
          />
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

Este objeto lo pasamos como propiedad o `prop` al atributo, que luego va a ser una propiedad de nuestro componente, y al final esto se va a
convertir a un objeto.

Para que no nos marque error al pasar como variable `ficha_medica`, la meteremos entre las llaves `{}` para poder interpolarla y pasarla en
dicha propiedad, en dicha `prop`.

Y veremos en la consola del navegador el objeto con la propiedad `ficha` y su objeto con diferentes datos.

Entonces, le podemos pasar cualquier información, tanto a nivel variable, texto, del **componente padre** que sería `App`, al
**componente hijo** que sería `TercerComponente`. Aunque luego, el tema de los componentes padres e hijos difiere un poco en React a como se
vería en otros frameworks.

## Mostrar `props` por pantalla

Mostramos los datos del objeto `props` así:

```jsx
export const TercerComponente = (props) => {
    console.log(props);

    return (
        <div>
            <h1>Comunicación entre componentes</h1>
            <ul>
                <li>{props.nombre}</li>
                <li>{props.apellidos}</li>
                <li>{props.ficha.grupo}</li>
                <li>{props.ficha.estado}</li>
            </ul>
        </div>
    )
}
```

Y veremos la información por pantalla. Pero es un poco largo estar escribiendo cada vez `props`, y para ahorrarnos este paso, podemos utilizar la **desestructuración** de JavaScript.

En lugar de poner `props`, utilizamos las llaves `{}` y podemos sacar la propiedad del objeto original y, desestructurarla, crear, y hacer de eso una variable para acceder directamente:

```jsx
export const TercerComponente = ({nombre, apellidos, ficha}) => {

    return (
        <div>
            <h1>Comunicación entre componentes</h1>
            <ul>
                <li>{nombre}</li>
                <li>{apellidos}</li>
                <li>{ficha.grupo}</li>
                <li>{ficha.estado}</li>
            </ul>
        </div>
    )
}
```

Aunque siempre tendremos que acceder al objeto `ficha` directamente, podemos hacer una doble desestructuración. Y veremos que el resultado es
el mismo.

Entonces, así podemos enviar datos desde un componente que sería `App` hasta el otro componente que sería `TercerComponente`, usando atributos
de HTML para pasar esa información en la etiqueta del componente, recibiendo como parámetro de la función del componente, recibiendo y
desestructurando esos datos, y luego, podemos imprimir los resultados o hacer lo que queramos con está información que nos llegue.