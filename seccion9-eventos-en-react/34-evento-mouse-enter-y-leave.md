# 34. Evento Mouse Enter y Leave

Hay más eventos de React que podríamos ver, de dar clic, de pasar por encima un elemento y tal, pero haría falta utilizar el estado de React y
eso ya es un **Hook** que veremos más adelante.

## Evento Mouse Enter

Otro pequeño ejemplo sin usar el estado ni ningún Hook, sería el evento `onMouseEnter`. Se capturaría cuando pasamos por encima de un elemento,
vamos a usar el evento, es decir, entrar y salir el ratón.

Crearemos un `<div id="caja">`:

```jsx
export const EventosComponente = () => {
  const hasDadoClick = (e, nombre) => {
    alert("Has dado click al botón !!" + nombre);
  }

  function hasDadoDobleClick(e) {
    alert("Has dado doble click!!");
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

      <div id="caja">
        {/**Evento onMouseEnter onMouseLeave */}
        Pasa por encima!!
      </div>
    </div>
  )
}
```

Entonces, cuando pasemos dentro de esta caja, va a pasar algo. Le daremos estilos a este identificador, podríamos usar clases pero será un
elemento único para que veamos el ejemplo. Nos iremos al `index.css` y le daremos estilos, una forma:

```css
#caja {
  width: 200px;
  height: 200px;
  border: 5px solid white;
  background-color: lightblue;
  text-align: center;
  line-height: 190px;
}
```

Ahora, aplicaremos los eventos y crearemos la función con un parámetro para evitar hacer dos funciones, y concatenar la acción:

```jsx
export const EventosComponente = () => {
  const hasDadoClick = (e, nombre) => {
    alert("Has dado click al botón !!" + nombre);
  }

  function hasDadoDobleClick(e) {
    alert("Has dado doble click!!");
  }

  const hasEntrado = (e, accion) => {
    alert(`Has ${accion} a la caja con el mouse!!`);
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
    </div>
  )
}
```

Obviamente, para que esto funcione tenemos que llamar al evento y llamar a la función.

Y esto funciona. Ahora lo haremos con `console.log()`'s para que lo veamos más fácil:

```jsx
const hasEntrado = (e, accion) => {
  console.log(`Has ${accion} a la caja con el mouse!!`);
}
```

Y esto también funciona. Ya tenemos otro evento capturado y esto puede servir para infinidad de cosas dentro del desarrollo de una aplicación
web.