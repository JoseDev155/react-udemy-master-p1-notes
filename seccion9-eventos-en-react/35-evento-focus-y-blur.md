# 35. Evento Focus y Blur

Vamos a ver los eventos `onBlur` y `onFocus`, son eventos muy interesantes, aquí ya vamos a usar un poquito de formularios.

## Evento `onFocus`

Nos creamos un párrafo y un `<input>` de tipo texto. Y le aplicaremos el `onFocus`.

El `onFocus` es cuando hacemps foco dentro de un campo. Y le pondremos un `placeholder`, que es el texto por defecto que viene, pero cuando nos
ponemos encima desaparece.

Y cuando hagamos `onFocus`, es decir, nos metemos dentro del `<input>`, queremos que automáticamente nos aparezca una alerta que diga
"**Estas dentro del input, mete tu nombre**".
Y para eso vamos a crear una función. Las funciones siempre hay que definirlas antes de renderizar la vista. Si solamente vamos a pasarle un
parámetro, no hacen falta los paréntesis `()`:

```jsx
export const EventosComponente = () => {
  const hasDadoClick = (e, nombre) => {
    alert("Has dado click al botón !!" + nombre);
  }

  function hasDadoDobleClick(e) {
    alert("Has dado doble click!!");
  }

  const hasEntrado = (e, accion) => {
    console.log(`Has ${accion} a la caja con el mouse!!`);
  }

  const estasDentro = e => {
    alert("Estas dentro del input, mete tu nombre!!");
  }

  return (
    <div>
      <h1>Eventos en React</h1>

      <p>
        {/**Evento click */}
        <button onClick={ e => hasDadoClick(e, "Victor") }>Dame click!</button>
      </p>

      <p>
        {/**Evento doble click */}
        <button onDoubleClick={ hasDadoDobleClick }>Dame doble click!</button>
      </p>

      <div id="caja" 
          onMouseEnter={ e => hasEntrado(e, "entrado") } 
          onMouseLeave={ e => hasEntrado(e, "salido") }
      >
        {/**Evento onMouseEnter onMouseLeave */}
        Pasa por encima!!
      </div>

      <p>
        <input type="text" onFocus={ estasDentro } placeholder="Introduce tu nombre..." />
      </p>
    </div>
  )
}
```

Nos vamos al `input` y nos pondemos dentro. Saltará la alerta, le damos **Aceptar**, metemos nuestros datos y nos salimos. Y cuando nos salimos,
ahí hay otro evento. Ese evento es el `onBlur`. Y si nos volvemos a meter, saltará la alerta otra vez (**NOTA MAS ABAJO**).

## Evento `onBlur`

Si aplicamos el `onBlur`, capturaría la acción de salir fuera de ese `input`. Podemos ejecutar también una función, que la vamos a crear.
Estos son eventos típicos de JavaScript de toda la vida, y el `onBlur` es cuando estamos fuera:

```jsx
export const EventosComponente = () => {
  const hasDadoClick = (e, nombre) => {
    alert("Has dado click al botón !!" + nombre);
  }

  function hasDadoDobleClick(e) {
    alert("Has dado doble click!!");
  }

  const hasEntrado = (e, accion) => {
    console.log(`Has ${accion} a la caja con el mouse!!`);
  }

  const estasDentro = e => {
    alert("Estas dentro del input, mete tu nombre!!");
  }

  const estasFuera = e => {
    alert("Estas FUERA del input, CHAO!!");
  }

  return (
    <div>
      <h1>Eventos en React</h1>

      <p>
        {/**Evento click */}
        <button onClick={ e => hasDadoClick(e, "Victor") }>Dame click!</button>
      </p>

      <p>
        {/**Evento doble click */}
        <button onDoubleClick={ hasDadoDobleClick }>Dame doble click!</button>
      </p>

      <div id="caja" 
          onMouseEnter={ e => hasEntrado(e, "entrado") } 
          onMouseLeave={ e => hasEntrado(e, "salido") }
      >
        {/**Evento onMouseEnter onMouseLeave */}
        Pasa por encima!!
      </div>

      <p>
        {/**Evento focus y blur */}
        <input type="text" 
               onFocus={ estasDentro } 
               onBlur={ estasFuera } 
               placeholder="Introduce tu nombre..." />
      </p>
    </div>
  )
}
```

Y esto funciona. Pero como constantemente estamos saliendo fuera del `input`, la alerta se ejecuta infinitamente, la cambiamos por un
`console.log()` para que no sea muy intrusivo:

```jsx
export const EventosComponente = () => {
  const hasDadoClick = (e, nombre) => {
    alert("Has dado click al botón !!" + nombre);
  }

  function hasDadoDobleClick(e) {
    alert("Has dado doble click!!");
  }

  const hasEntrado = (e, accion) => {
    console.log(`Has ${accion} a la caja con el mouse!!`);
  }

  const estasDentro = e => {
    console.log("Estas dentro del input, mete tu nombre!!");
  }

  const estasFuera = e => {
    console.log("Estas FUERA del input, CHAO!!");
  }

  return (
    <div>
      <h1>Eventos en React</h1>

      <p>
        {/**Evento click */}
        <button onClick={ e => hasDadoClick(e, "Victor") }>Dame click!</button>
      </p>

      <p>
        {/**Evento doble click */}
        <button onDoubleClick={ hasDadoDobleClick }>Dame doble click!</button>
      </p>

      <div id="caja" 
          onMouseEnter={ e => hasEntrado(e, "entrado") } 
          onMouseLeave={ e => hasEntrado(e, "salido") }
      >
        {/**Evento onMouseEnter onMouseLeave */}
        Pasa por encima!!
      </div>

      <p>
        {/**Evento focus y blur */}
        <input type="text" 
               onFocus={ estasDentro } 
               onBlur={ estasFuera } 
               placeholder="Introduce tu nombre..." />
      </p>
    </div>
  )
}
```

Esto funciona correctamente y se imprimen los mensajes en la consola del navegador.
Además, si revisamos en la extensión en el apartado de **Components**, veremos indicadas las `props` en aquellos componentes que las poseen.

Y esos son los eventos que estamos capturando con el `onFocus` y el `onBlur`.

## Notas

Las alertas en el evento `onBlur` y `ònFocus` se ejecutan infinitamente, pero al cambiar el `alert()` por un `console.log()` esto no pasa.
Desconozco el por qué.