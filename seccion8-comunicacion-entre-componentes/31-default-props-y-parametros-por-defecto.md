# 31. Default props y parámetros por defecto

Aparte de poder validar las props, podemos pasar parámetros por defecto.

## Manera clásica

Como hacíamos en cualquier función:

```jsx
export const TercerComponente = ({
                                    nombre = "Víctor",
                                    apellidos = "Robles",
                                    ficha
                                }) => {
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
    nombre: PropTypes.string.isRequired,
    apellidos: PropTypes.string.isRequired,
    ficha: PropTypes.object
}
```

Para que por defecto venga ese valor. En el caso de que no recibamos estos dos parámetros, ya vamos a tener un valor por defecto, por lo
tanto, la validación se cumpliría.

Y vamos a quitarle estos dos parámetros, dos `props`, en el `App.js`:

```jsx
<TercerComponente 
    ficha={ficha_medica} 
/>
```

Y seguirá viendose igual, porque por defecto están viniendo unso valores. Si lo cambiamos:

```jsx
export const TercerComponente = ({
                                    nombre = "Pepe",
                                    apellidos = "Robles",
                                    ficha
                                }) => {
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
```

Y va a funcionar igual. Se cambia automáticamente ese valor porque por defecto, cuando no llega esta `prop`, le damos ese valor.

## Usando `defaultProps`

Le podemos indicar aquí los valores por defecto:

```jsx
export const TercerComponente = ({
                                    nombre,
                                    apellidos,
                                    ficha
                                }) => {
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

TercerComponente.defaultProps = {
    nombre: "Juan",
    apellidos: "Martinez"
}
```

Así que si no nos llegan esos datos, se están cambiando, sin necesidad de ponerlo como parámetro por defecto, o como valor por defecto de un
parámetro.

Anteriormente, estabamos utilizando los parámetros por defecto en una función, que es lo típico, se pueden utilizar en la desestructuración sin
ningún problema.

Aunque si estamos requiriendo unos parámetros, se los pasemos:

```jsx
<TercerComponente 
    nombre="Víctor" 
    apellidos="Robles" 
    ficha={ficha_medica} 
/>
```

Y automáticamente se reflejen en la página.