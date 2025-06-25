# 33. Evento doble click

Copiamos el botón de nuestro componente para usarlo en el ejemplo del evento **doble click**.

Cuando ejecutemos el conle clic, es decir, `onDoubleClick`, podemos ejecutar perfectamente un evento ya vamos a llamar a una función:

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

      {/**Evento click */}
      <button onClick={ e => hasDadoClick(e, "Victor") }>Dame click!</button>

      {/**Evento doble click */}
      <button onDoubleClick={ hasDadoDobleClick }>Dame doble click!</button>
    </div>
  )
}
```

Lo estándar, es usar `const` para definir funciones con JavaScript moderno.

En este caso, no hace falta capturar el evento. Simplemente llamando a la función el evento ya se pasa solo.

Si le damos clic, no hace nada. Si le damos doble clic, nos saca automáticamente el mensaje de alerta.

Pare tener un poco de separación entre los eventos, los meteremos dentro de un párrafo:

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
    </div>
  )
}
```

Y veríamos mejor los botones en la vista.