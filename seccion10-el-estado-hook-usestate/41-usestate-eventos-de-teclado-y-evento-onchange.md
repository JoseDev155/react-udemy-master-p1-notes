# 41. useState, eventos de teclado y evento onChange

En el componente `MiPrimerEstado.js`, usaremos eventos para cambiar el `nombre` sin tener que darle clic al botón.

Actualizamos el nombre del botón:

```jsx
<button onClick={ cambiarNombre }>Cambiar nombre por Fran</button>
```

Entonces, a la función le pasamos como parámetros, tanto el evento como el nombre. Y luego, se lo pasamos como parámetro a la función
`setNombre`:

```jsx
const cambiarNombre = (e, nombreFijo) => {
    setNombre(nombreFijo);
}
```

Y luego, en el `onClick`, hacemos una función para pasar el evento e invocar la función `cambiarNombre()`, y le pasamos el evento y el
`nombreFijo`:

```jsx
return (
    <div>
        <h3>Componente: MiPrimerEstado</h3>
        <strong>
            {nombre}
        </strong>
        &nbsp;
        <button onClick={ e => cambiarNombre(e, "Francisco") }>Cambiar nombre por Fran</button>
    </div>
  )
```

Y esto funciona correctamente.

Pero ahora, haremos un `input`, que mientras vayamos escribiendo, nos vaya modificando el comportamiento o el nombre que aparece por pantalla.

Entonces, definiremos un `<input>` de tipo texto y le pondremos un `placeholder`:

```jsx
return (
    <div>
        <h3>Componente: MiPrimerEstado</h3>
        <strong>
            {nombre}
        </strong>

        &nbsp;
        <button onClick={ e => cambiarNombre(e, "Francisco") }>Cambiar nombre por Fran</button>
        &nbsp;
        <input type="text" placeholder='Cambia el nombre' />
    </div>
  )
```

Y le ponemos un espacio para que se vea un poco más limpio en la interfaz.

Entonces, queremos que al escribir el nombre en el `<input>`, se refleje en el Estado. Para eso usaremos el evento `onChange` que existe dentro de
React y dentro de JavaScript.

## Evento onChange y onKeyUp

Lo que va a hacer es que, cada vez que vayamos tecleando se genere un cambio, y mientras que se vayan generando cambios, lo que vamos a hacer
es ejecutar la función `cambiarNombre()`.

Podemos hacer esto o utilizar otros eventos. Por ejemplo, **Eventos de Formulario**, tenemos el `onChange` (el que vamos a usar).

### Evento onKeyUp

Pero tenemos también los **Eventos del Teclado** como el `onKeyUp`, es decir, cada vez que levantemos el dedo de una tecla, se va a ver
reflejado en la pantalla.
Y vamos a llamar a la función `cambiarNombre()`, y para poder conseguir el dato que estamos escribiendo dentro del `<input>`, tendríamos que
acceder al evento. Primero, le pasaríamos el evento y le vamos a pasar como valor de `nombreFijo` el `e.target.value`.

Con `e.target.value`, estamos accediendo al objeto del evento, al `target` que es el `<input>` y el `value` que se le está rellenando a
este propio `<input>`. Así le pasamos lo que estamos escribiendo dentro del `<input>`:

```jsx
return (
    <div>
        <h3>Componente: MiPrimerEstado</h3>
        <strong>
            {nombre}
        </strong>

        &nbsp;
        <button onClick={ e => cambiarNombre(e, "Francisco") }>Cambiar nombre por Fran</button>
        &nbsp;
        <input type="text" onKeyUp={ e => cambiarNombre(e, e.target.value) } placeholder='Cambia el nombre' />
    </div>
  )
```

Si empezamos a escribir en el `<input>`, veremos como se reflejan los cambios en el `nombre` mientras escribimos. Si lo borramos, se va
borrando.

Y si dentro de `cambiarNombre()`, mostramos en la consola del navegador el objeto `e.target`:

```jsx
const cambiarNombre = (e, nombreFijo) => {
    setNombre(nombreFijo);
    console.log(e.target);
}
```

Veremos lo que tiene dentro. Si revisamos en la consola del navegador y le damos clic al botón, veremos que el `target` del evento `onClic`, es
el `<button>`, y no hay ningún `value`.
Pero si escribimos en el `<input>`, se está ejecutando varias veces esa función, pero el `target` es el `<input>`. Y si lo desplegamos, tenemos
muchas propiedades, entre ellas, una que es `value` con un dato dentro que es lo que ingresamos en el `<input>`. Por tanto, estamos accediendo a
esa propiedad del objeto del evento.

El evento está vinculado al elemento del DOM al cual se lo estamos aplicando. Así podemos a acceder a ello y mostrar todo.

Y esto es totalmente **reactivo**, es decir, metemos un dato e instantáneamente se está cambiando.

### Evento onChange

De igual forma, si utilizáramos el `onChange`, también funcionaría, aunque el evento sería un poco distinto:

```jsx
return (
    <div>
        <h3>Componente: MiPrimerEstado</h3>
        <strong>
            {nombre}
        </strong>

        &nbsp;
        <button onClick={ e => cambiarNombre(e, "Francisco") }>Cambiar nombre por Fran</button>
        &nbsp;
        <input type="text" onChange={ e => cambiarNombre(e, e.target.value) } placeholder='Cambia el nombre' />
    </div>
  )
```

También funciona igual, lo único que el cambio se ejecuta instantáneamente.

Porque cuando utilizamos `onKeyDown` y el `onKeyUp`, es cuando se produce esa pulsación de teclado, es decir, hemos estado usando el
`onKeyUp`, es justo cuando levantamos el dedo de la tecla cuando se produce el cambio. Si utilizaramos el `onKeyDown`, sería justo cuando la
pulsamos.
Entonces, hay diferencias entre los eventos.

Y el `onKeyPress` es justo cuando la presionamos.

El `onChange`, reacciona a absolutamente todo y el cambio es mucho más instantáneo.

También, podríamos modificar los estilos del `nombre` para que se viera de otro color o se representara de otra manera. Podríamos aplicarle una clase cin el atributo `className`:

```jsx
return (
    <div>
        <h3>Componente: MiPrimerEstado</h3>
        <strong className="label">
            {nombre}
        </strong>

        &nbsp;
        <button onClick={ e => cambiarNombre(e, "Francisco") }>Cambiar nombre por Fran</button>
        &nbsp;
        <input type="text" onChange={ e => cambiarNombre(e, e.target.value) } placeholder='Cambia el nombre' />
    </div>
  )
```

Y luego, lo cambiamos en el `App.css`:

```css
.label {
  background-color: lightblue;
  border-radius: 5px;
  padding: 5px;
  color: #444;
}
```

Y veremos los cambios aplicados al `nombre`.