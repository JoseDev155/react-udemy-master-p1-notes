# 50. Montar y desmontar componentes

## Continuación de ejemplo del contador

Queremos que cuando se supere el número de iteraciones de `10` del uso del efecto y del `contador`, cuando se supere el número `20` en el
`contador`, queremos que se muestre otro componente.

Queremos que aquí abajo, justo después de poner todo esto, queremos que se nos muestre otro componente. Pero para eso tenemos que hacer una
condición por aquí. Podemos usar la condición ternaria que hemos hecho o también utilizando el `&&` que significa lo mismo:

```jsx
return (
    <div>
        <h1>El efecto - Hook useEffect</h1>
        <strong>{usuario}</strong>
        <strong className={ contador >= 10 ? 'label label-green' : 'label' }>{fecha}</strong>
        <p>
            <input type="text" 
                   onChange={ modUsuario } 
                   placeholder="Cambia el nombre" 
            />

            <button onClick={cambiarFecha}>Cambiar fecha</button>
        </p>

        { contador >= 20 && "Hemos superado el 20 en el contador" }
    </div>
)
```

Si hacemos `20` cambios, nos aparece el mensaje por pantalla.

Este mensaje queremos que venga de otro componente, queremos que a lo mejor en lugar de que sea solo un texto, a lo mejor queremos desplegar un
formulario o queremos hacer algo.

### Creando un nuevo componente

Creamos el componente que se llamará `AvisoComponent.js`. Y ahora, veremos para qué sirve el `useEffect` a nivel de montar y desmontar componentes.

Porque podemos detectar cuando se carga un componente, y cuando se descarga o cuando se quita de la interfaz.

Y con la instrucción `rafc` se nos crea la estructura base automáticamente:

```jsx
import React from 'react'

export const AvisoComponent = () => {
  return (
    <div>AvisoComponent</div>
  )
}
```

Lo modificamos así:

```jsx
export const AvisoComponent = () => {
  return (
    <div>
        <h1>Hemos superado los 20 cambios</h1>
        <button>Mostrar alerta</button>
    </div>
  )
}
```

### Cargando componente

Utilizamos la etiqueta del componente en el `PruebasComponent.js` así:

```jsx
{ contador >= 20 && <AvisoComponent /> }
```

El `import` se ha hecho arriba:

```jsx
import { AvisoComponent } from './AvisoComponent';
```

Cuando superemos los 20 cambios, nos aparece cargado el mensaje.

Cambiamos el `<h1>` a un `<h3>`, le metemos un `<hr />`:

```jsx
export const AvisoComponent = () => {
  return (
    <div>
        <hr />
        <h3>Hemos superado los 20 cambios</h3>
        <button>Mostrar alerta</button>
    </div>
  )
}
```

Y vamos a cambiar el comportamiento para que no sea cuando llguemos a `20` cambios, sino que cuando el `usuario` sea igual a algo:

```jsx
{ usuario == "VICTOR" && <AvisoComponent /> }
```

Y cambiamos el mensaje en el componente `AvisoComponent.js`:

```jsx
export const AvisoComponent = () => {
  return (
    <div>
        <hr />
        <h3>Saludos Víctor ¿Que tal estas?</h3>
        <button>Mostrar alerta</button>
    </div>
  )
}
```

Si cambiamos el nombre, no pasa nada, pero si ponemos **VICTOR**, si que nos muestra el mensaje.

Queremos mostrar también un aviso de que hemos montado el componente. Antes haremos lo del botón, lo de la alerta, con el `onClick` y
ejecutamos la alerta. Pero lo ejecutaremos dentro de una función para que React no lo ejecute múltiples veces antes de que queramos:

```jsx
export const AvisoComponent = () => {
  return (
    <div>
        <hr />
        <h3>Saludos Víctor ¿Que tal estas?</h3>
        <button onClick={e => {
          alert("Bienvenido!!")
        }}>Mostrar alerta</button>
    </div>
  )
}
```

Entonces, si actualizamos la pantalla ahora, ponemos **VICTOR**, le damos a **Mostrar alerta** y se ejecuta la alerta.

Ahora queremos mostrar un mensaje, una alerta, cuando se monte el componente y cuando se desmonte.

### Montando y desmontando el componente

Cuando ponemos el nombre **VICTOR**, se monta el componente, pero si lo quitamos se desmonta el componente.

Para detectar esas dos cosas usaremos el `useEffect`. Se nos hace la importación automática en VS Code.

Y dentro, como parámetro del `useEffect`, tenemos una función de **callback**, anónima, ese sería el primer parámetro, y el segundo, sería
cuando queremos que se lance esto. Como no tenemos otro estado para comprobar, queremos que se lance una sola vez cuando carguemos nuestro
componente. Es decir, haremos:

```jsx
import React, { useEffect } from 'react'

export const AvisoComponent = () => {
  useEffect(() => {
    alert("El componente AvisoComponent está montado!!");
  }, []);
  
  return (
    <div>
        <hr />
        <h3>Saludos Víctor ¿Que tal estas?</h3>
        <button onClick={e => {
          alert("Bienvenido!!")
        }}>Mostrar alerta</button>
    </div>
  )
}
```

Si ponemos cosas no pasa nada, pero si ponemos **VICTOR** se muestra la alerta y se monta el componente.

Y luego queremos detectar cuando se desmonta. Es decir, el `useEffect` detecta cuando el componente se monta y se ejecuta una sola vez porque le
estamos pasando precisamente el segundo parámetro `[]` y no estamos vinculando ningún estado a este efecto.

El `[]` es para meter aquí los estados que queremos estar detectando siempre, para que el efecto esté vinculado.

Pero cuando se desmonta, podemos detectarlo también dentro del `useEffect`. Lo podemos detectar en el `return`, si hacemos el `return`
de una función anónima también, podemos ejecutar y lanzar la funcionalidad que queramos cuando el componente se desmonta:

```jsx
useEffect(() => {
    alert("El componente AvisoComponent está montado!!");

    return () => {
      alert("COMPONENTE DESMONTADO!!!");
    }
}, []);
```

Y la lógica que metemos dentro de la función anónima, se van a ejecutar cuando el componente se desmonte. Esto nos puede servir para enviar un
email, para dejar de seguir a alguien, para lanzar una petición **AJAX**, etc.

Ahora, si ponemos lo que sea no pasa nada. Pero si ponemos **VICTOR** veremos la alerta de montar el componente, pero si ponemos otra cosa o lo
borramos, nos dice **COMPONENTE DESMONTADO!!!** porque ya no está cargado en la aplicación.

## Métodos de trabajo y, montar y desmontar componentes en otros frameworks

Si hemos trabajado con React anteriormente, teníamos antes otros métodos para hacer esto mismo. No era solamente usando el `useEffect`, teníamos
funciones relacionadas con el montar y desmontar componentes, pero ahora, se hace de esta manera.

En otros frameworks de JavaScript, como **Angular**, teníamos el método `ngOnInit()` para montar y el `ngOnDestroy()` que se lanzaba cuando se
desmontaba el componente.

Osea, todos estos hooks es algo que existe ya en todos los frameworks. El tema de los hooks no es algo revolucionario de React, es un cambio que
se hizo, que fue revolucionario a nivel cómo percibia la gente el trabajo con React.

Pero los hooks y las acciones que se lanzan cuando pasa algo en el ciclo de vida de un componente es algo que siempre ha existido.

Por ejemplo, el `useEffect`, también en Angular existe el `ngDoCheck()`, que lo que hace es comprobar continuamente cambios en el componente.

Osea, todo esto existe ya, pero React lo trata de otra manera y le ha puesto un nombre diferente y lo ha simplificado un poco el tema de cómo
usarlo.

Pero el tema de los hooks se usa en todos los frameworks y es algo que ya existía también antes cuando se usaba solamente clases para programar
con React.