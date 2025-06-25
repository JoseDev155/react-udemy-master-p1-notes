# 32. Evento Click en React

Los **eventos**, que tenemos también en JavaScript, es cuando sucede una acción, que pase algo.

Por ejemplo: si le damos clic a un botón, tiene que ejecutarse una función, modificamos el texto dentro de un campo de un formulario, tiene
que pasar algo o se va a ejecutar una función cuando eso pase.
Presionamos una tecla, puede ejecutarse también una función, en el clic, en el doble clic, hay un motón de eventos que podríamos aplicar. Tanto a
eventos como hay en JavaScript los podemos utilizar dentro de React.

## Información de eventos en JavaScript

Para saber más acerca de esto, podemos buscar "**js events** en Google, y nos va a aprecer la **Referencia de Eventos** y veremos muchos eventos
relacionados con JavaScript. Los más conocidos son el `blur`, el `change`, el `click`.

## Información de eventos en React

Buscamos "**events react** en Google, también podemos ver los eventos que hay dentro de React. Los más conocidos son:

* Eventos del Ratón: onClick, onDoubleClick, onDrag, etc.
* Eventos del Teclado.
* Eventos de Formulario.
* Y hay muchos más.

Hay infinidad de eventos para casi todo, porque ahora con las pantallas y los dispositivos móviles, nosotros podemos caturar prácticamente todas
las acciones que podamos hacer dentro de una pantalla, se pueden capturar.

Vamos a ver los más importantes.

Para trabajar con los eventos, vamos a crear un nuevo componente llamado `EventosComponente.js` y aquí vamso a ejecutar el `rafc`. Y ya tenemos
nuestro componente creado:

```jsx
import React from 'react'

export const EventosComponente = () => {
  return (
    <div>EventosComponente</div>
  )
}
```

Añadimos un `<h1>` y un comentario:

```jsx
export const EventosComponente = () => {
  return (
    <div>
      <h1>Eventos en React</h1>

      {/**Evento click */}
    </div>
  )
}
```

## Evento Click

Es tan sencillo como que, cuando le demos clic a un elemento, tiene que pasar algo. Para utilizarlo, crearemos un botón y le ponemos el evento
`onClick`, muy parecido a cuando lo hacemos en HTML.

Y entre las llaves `{}`, podemos ejecutar una función que tengamos definida fuera del `return` o mismamente ejecutar aquí dentro una función
anónima:

```jsx
export const EventosComponente = () => {
  return (
    <div>
      <h1>Eventos en React</h1>

      {/**Evento click */}
      <button onClick={() => {
        console.log("Hola, soy un evento click");
      }}>Dame click!</button>
    </div>
  )
}
```

Y esto se va a ejecutar y se va a ver tantas veces como le demos clic al botón. Una vez definido el `onClick`, cerramos la etiqueta y le ponemos
"**Dame click!**".

**NOTA**: En siguientes clases, organizaremos los eventos diferente, tendremos una carpeta de componentes, y dentro, tendremos ahí todos
nuestros componentes organizados.

Ahora llamamos al componente dentro de `App.js` y automáticamente en VS Code, se nos añade el `import`:

```jsx
import { EventosComponente } from './EventosComponente';

function App() {
  const ficha_medica = {
    altura: "187cm",
    grupo: "H+",
    estado: "Bueno",
    alergias: "Ninguna"
  }

  const numero = 123456;

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
          <EventosComponente />
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

Ya tenemos nuestro componente y el botón en la pantalla, si nos vamos a la consola del navegador y le damos clic al botón, vamos a ver lo que ha
ejecutado ese evento de clic. Cada vez que le damos clic, el número de ves que se ha ejecutado el evento irá aumentando.

También podemos ver lo que trae el evento dentro. Si le pasamos la `e` como parámetro, podemos hacer un `console.log(e)`, que sería capturar el
evento como tal:

```jsx
export const EventosComponente = () => {
  return (
    <div>
      <h1>Eventos en React</h1>

      {/**Evento click */}
      <button onClick={(e) => {
        console.log(e);
        console.log("Hola, soy un evento click");
      }}>Dame click!</button>
    </div>
  )
}
```

Ahora, si le damos clic al botón, veremos un objeto cuyo evento es el `onClick` y tendremos una serie de propiedades que le podríamos llegar a
aplicar.

No es muy recomendado definir en el evento una función anónima y meter lógica. Porque queda muy desordenado.
Para eso, podemos definir una función dentro de nuestro componente.

## Función vinculada a un evento

Normalmente, se suele llamar a las funciones que están vinculadas a eventos **handle+LoQueSea**.

Podemos definir la función de la forma clásica, o de una forma más limpia, crear una constante, y dentro, definir la función anónima. Y la
llamamos dentro del botón:

```jsx
export const EventosComponente = () => {
  const hasDadoClick = (e) => {
    alert("Has dado click al botón !!");
  }

  return (
    <div>
      <h1>Eventos en React</h1>

      {/**Evento click */}
      <button onClick={ hasDadoClick }>Dame click!</button>
    </div>
  )
}
```

En este caso, no le tenemos que pasar parámetros. A no ser que le especifiquemos uno para algún dato que haya en la vista o lo que sea.
Pero en principio, no es necesario.

Ahora, si damos clic al botón, nos aparece la alerta.

Si quisieramos pasarle un parámetro, por ejemplo, un `nombre` y mostrarlo en el `alert()`:

```jsx
export const EventosComponente = () => {
  const hasDadoClick = (e, nombre) => {
    alert("Has dado click al botón !!" + nombre);
  }

  return (
    <div>
      <h1>Eventos en React</h1>

      {/**Evento click */}
      <button onClick={ hasDadoClick("Victor") }>Dame click!</button>
    </div>
  )
}
```

Esto no va a funcionar. Ejecuta directamente el método sin haberle dado clic, al llegar a esa parte del código, lo ejecuta. ¿Qué está pasando? La
forma en que está definida la función hace que precisamente se ejecute sola, la está llamando directamente.

Para que funcione vinculado al evento, lo que tenemos que hacer es pasarle como parámetro el evento, y entonces, llamar a esa función de
esta manera:

```jsx
export const EventosComponente = () => {
  const hasDadoClick = (e, nombre) => {
    alert("Has dado click al botón !!" + nombre);
  }

  return (
    <div>
      <h1>Eventos en React</h1>

      {/**Evento click */}
      <button onClick={ e => hasDadoClick("Victor") }>Dame click!</button>
    </div>
  )
}
```

Es decir, llamarla dentro de una función anónima, no llamarla directamente. De está manera si que nos va a funcionar.

Ahora, para que correspondan los parámetros hay que pasar el evento como primer parámetro y el `nombre` como segundo parámetro:

```jsx
export const EventosComponente = () => {
  const hasDadoClick = (e, nombre) => {
    alert("Has dado click al botón !!" + nombre);
  }

  return (
    <div>
      <h1>Eventos en React</h1>

      {/**Evento click */}
      <button onClick={ e => hasDadoClick(e, "Victor") }>Dame click!</button>
    </div>
  )
}
```

Y si le damos clic al botón, pondría el nombre.