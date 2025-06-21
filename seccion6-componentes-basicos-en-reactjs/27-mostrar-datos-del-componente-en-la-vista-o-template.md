# 27. Mostrar datos del componente en la vista o template

Quitaremos los duplicados del componente que hicimos en la clase pasada.

## Pasar datos de nuestro componente a nuestra vista

Si tenemos varias propiedades, varias variables dentro de la función `MiComponente` y queremos enviarlas para imprimirlas en el `return`.

Variables que pueden cambiar de valor y queremos estar mostrandolo por pantalla en cada momento.

Las variables declaradas con `const` no pueden actualizar su valor, las variables declaradas con `let` si. Crearemos unas variables en el
componente:

```jsx
const MiComponente = () => {
    let nombre = "Víctor";
    let web = "victorroblesweb.es";
};
```

## Interpolar variables

Ahora, interpolaremos las variables. **Interpolar** es tomar el contenido de una variable y mostrarlo dentro de una plantilla.

Para ello, usamos las llaves `{}`:

```jsx
const MiComponente = () => {
    let nombre = "Víctor";
    let web = "victorroblesweb.es";

    return (
        <div className="mi-componente">
            <hr />
            <h2>Componente creado</h2>
            <h3>Datos del usuario:</h3>
            <ul>
                <li>Nombre: <strong>{nombre}</strong></li>
                <li>Web: <strong>{web}</strong></li>
            </ul>
            <p>Este es mi primer componente</p>
            <ul>
                <li>
                    React
                </li>
                <li>
                    Angular
                </li>
                <li>
                    Vue
                </li>
            </ul>
        </div>
    );
};
```

Veremos el contenido de las variables impreso por pantalla.

## Imprimir un objeto JSON

Creamos el objeto:

```jsx
const MiComponente = () => {
    let nombre = "Víctor";
    let web = "victorroblesweb.es";

    let usuario = {
        nombre: "Víctor",
        apellidos: "Robles",
        web: "victorroblesweb.es"
    };
};
```

No podemos imprimir directamente el objeto:

```jsx
<li>Nombre: <strong>{usuario}</strong></li>
```

Porque nos generaría un error, si inspeccionamos en la consola del navegador veremos el error `Objects are not valid as a React child`. Pero
las `keys` si las podemos utilizar.

Para imprimir el objeto completo debemos usar `JSON.stringify`:

```jsx
<li>Nombre: <strong>{JSON.stringify(usuario)}</strong></li>
```

Dentro de las llaves, podemos poner el código de JavaScript que queramos. Veremos que se imprimirá por pantalla el objeto completo, como
`string`.

Pero lo imprimiremos usando las `keys`:

```jsx
const MiComponente = () => {
    let nombre = "Víctor";
    let web = "victorroblesweb.es";

    let usuario = {
        nombre: "Víctor",
        apellidos: "Robles",
        web: "victorroblesweb.es"
    };

    return (
        <div className="mi-componente">
            <hr />
            <h2>Componente creado</h2>
            <h3>Datos del usuario:</h3>
            <ul>
                <li>Nombre: <strong>{usuario.nombre}</strong></li>
                <li>Apellidos: <strong>{usuario.apellidos}</strong></li>
                <li>Web: <strong>{usuario.web}</strong></li>
            </ul>
            <p>Este es mi primer componente</p>
            <ul>
                <li>
                    React
                </li>
                <li>
                    Angular
                </li>
                <li>
                    Vue
                </li>
            </ul>
        </div>
    );
};
```

Y veremos por pantalla los datos del objeto `usuario`.

Mencionar también que podemos ejecutar funciones dentro del componente:

```jsx
const MiComponente = () => {
    let nombre = "Víctor";
    let web = "victorroblesweb.es";

    let usuario = {
        nombre: "Víctor",
        apellidos: "Robles",
        web: "victorroblesweb.es"
    };

    console.log(usuario);

    return (
        <div className="mi-componente">
            <hr />
            <h2>Componente creado</h2>
            <h3>Datos del usuario:</h3>
            <ul>
                <li>Nombre: <strong>{usuario.nombre}</strong></li>
                <li>Apellidos: <strong>{usuario.apellidos}</strong></li>
                <li>Web: <strong>{usuario.web}</strong></li>
            </ul>
            <p>Este es mi primer componente</p>
            <ul>
                <li>
                    React
                </li>
                <li>
                    Angular
                </li>
                <li>
                    Vue
                </li>
            </ul>
        </div>
    );
};
```

Y mostraremos el objeto `usuario` en la consola del navegador.