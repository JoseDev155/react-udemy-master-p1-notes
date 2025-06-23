# 30. PropTypes y validación de props

Cuando hacemos uso de las `props` para comunicar componentes, tenemos la posibilidad de validar esas `props` y poner filtros para validar esa
información.

## Validando con PropTypes

Es un objeto, que es un módulo que ya viene dentro de React. Lo importamos, y vamos a aplicarle las `PropTypes` al objeto
`TercerComponente` e indicarle a cada `prop` lo que queremos que lleve dentro.

Para saber qué datos podemos validar, vamos a Google y buscamos "**proptypes react**", y en la documentación, buscamos
**Verificación de tipos con PropTypes**, y veremos el tipo de validaciones que podemos hacer.

En este caso, queremos validar un tipo `object` y un tipo `string`. Es tan sencillo como utilizar el objeto `PropTypes` y la propiedad referente
al tipo de dato que queremos validar.

```jsx
import React from 'react'
import PropTypes from "prop-types"

export const TercerComponente = ({nombre, apellidos, ficha}) => {
    // console.log(props);

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

TercerComponente.propTypes = {
    nombre: PropTypes.string,
    apellidos: PropTypes.string,
    ficha: PropTypes.object
}
```

También podemos indicarle que sea un dato reqierido. Si no escribimos empezando en minúscula `propTypes` en nuestro componente, esto nos dará
un error. Cuando vamos a utilizar el objeto para validar, empieza en mayúsculas `PropTypes`.

Si al componente en `App.js`, le pasamos un string que contenga un número, si nos va a dejar:

```jsx
<TercerComponente 
    nombre="1" 
    apellidos="Robles" 
    ficha={ficha_medica} 
/>
```

Pero si le pasamos una variable que sea un número:

```jsx
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
          <TercerComponente 
            nombre={numero} 
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

Nos va a generar un error, ya que le estamos pasando un tipo `number` a `nombre`. Para que esto no pase, le tenemos que pasar el tipo de dato
correcto.

Si le quitamos una de las `props` al componente:

```jsx
<TercerComponente 
    apellidos="Robles" 
    ficha={ficha_medica} 
/>
```

No habrá ningún inconveniente. Pero si nosotros le indicamos en la validación de `PropTypes` que es `isRequired`:

```jsx
TercerComponente.propTypes = {
    nombre: PropTypes.string.isRequired,
    apellidos: PropTypes.string,
    ficha: PropTypes.object
}
```

Ya es obligatorio que está `prop` esté si o si, y con un contenido si o si. Porque si no, la validación no la estamos cumpliendo.

Es importante definir estas validaciones de las `props`, ya que si estamos trabajando en un equipo grande para evitar que un compañero se le
olvide pasar cierta propiedad a cierto componente.

En un proyecto que estemos trabajando nosotros solos, a lo mejor no hacen falta. ¿Es recomendable tenerlo? Sí, pero no hace falta.

Entonces, los datos más importantes, `nombre` y `apellidos`, si van a ser `isRequired` pero el del objeto no:

```jsx
TercerComponente.propTypes = {
    nombre: PropTypes.string.isRequired,
    apellidos: PropTypes.string.isRequired,
    ficha: PropTypes.object
}
```

Ya lo hemos puesto bien y no nos muestra ningún error en la consola del navegador.

## Notas

En la versión actual de React que es la 19, no muestran mensaje de error las `PropTypes`. Desconozco la razón de ello.