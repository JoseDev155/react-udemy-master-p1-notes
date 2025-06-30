# Resolviendo el ejercicio - Parte 2

## 5. Validar que el año sea un numero y que sea requerido (prop)

Sería validar la `prop`. Lo que haremos va a ser importar `PropTypes` en el componente `EjercicioComponent.js`:

```jsx
import PropTypes from "prop-types"
```

Y ahora, utilizaremos la validación con el componente y la propiedad `year`:

```jsx
EjercicioComponent.propTypes = {
  year: PropTypes.number.isRequired
}
```

De esta manera, siempre se va a estar validando que el año llegue correctamente.

Punto cinco, hecho.

## 6. Cambiar el año mediante un input de texto y que se cambie dinamicamente

Para ello, nos vamos a crear otro párrafo y aquí creamos el `<input>` con un `placeholder`. Y vamos a estar trabajando con el evento
`onChange`.

Lo que vamos a hacer, es que cada vez que toquemos algo del `<input>`, que se cambie automáticamente mediante una función. Entonces, nos creamos
una función anónima dentro recogiendo el evento e invocamos una función que vamos a crear que se va a llamar `cambiarYear()`.

Le podemos pasar el evento y el valor que tiene el campo, pero lo podemos hacer más sencillo. Es decir, podemos simplemente llamar a la función `cambiarYear()` y dentro de ella acceder, a los datos del evento,
y acceder al `<input>` y a su `value`:

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
        <p>Cambiar año: 
          <input 
          onChange={ cambiarYear } 
          type="text" 
          placeholder='Cambia el año' />
        </p>
    </div>
)
```

Ahora definimos la función, recibiendo el evento:

```jsx
const cambiarYear = e => {
    let dato = e.target.value;

    setYearNow(dato);
}
```

Entonces, si modificamos el año, se cambia perfectamente. Pero si le metemos un texto también va a funcionar, y esto no queremos que pase.

Vamos a validar que sean números.

Dentro de la propia función, haremos un `if` y usaremos el objeto `Number` para comprobar si es un entero con el método `isInteger()` (ya
que estamos trabajando con años), y si esto no se cumple, le pasaremos el `year` que nos llega en la función del componente como `prop`, ya que
ese dato va a ser un dato válido porque nos llega de una función de fecha:

```jsx
const cambiarYear = e => {
    let dato = e.target.value;

    if (Number.isInteger(dato)) {
      setYearNow(dato);
    } else {
      setYearNow(year);
    }
}
```

Ahora, no nos funciona ya que el valor del `<input>` es texto (`string`), entonces, haremos un `parseInt()` del valor que recogemos
como `value`:

```jsx
const cambiarYear = e => {
    let dato = parseInt(e.target.value);

    if (Number.isInteger(dato)) {
      setYearNow(dato);
    } else {
      setYearNow(year);
    }
  }
```

Así, lo convertimos a un número entero. Ahora, sí funciona.

Punto seis, hecho.