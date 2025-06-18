# 8. Flexbox

**Flexbox** es una nueva técnica de maquetación con CSS que nos permite crear un layout y organizar elementos de mejor manera dentro de una
página.

## Ejemplo de Flexbox

Creamos la carpeta `repaso-flexbox/` y creamos dos archivos: `index.html` y `styles.css`.

### Estructura básica de HTML

Estructura del `index.html`:

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE-edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aprendiendo Flexbox</title>
</head>
<body>
    <h1>Aprendiendo FLEXBOX con Víctor Robles</h1>

    <section class="flex-container">
        <div class="caja">
            Caja 1
        </div>
        <div class="caja">
            Caja 2
        </div>
        <div class="caja">
            Caja 3
        </div>
        <div class="caja">
            Caja 4
        </div>
    </section>
</body>
</html>
```

El `flex-conatiner` es lo que va a contener ese layout con flex que haremos. Dentro del `<section>`, creamos diferentes `<div>`'s y les
ponemos la clase `caja`.

Le ponemos un background al `<body>`:

```css
body {
    background-color: beige;
}
```

Y vinculamos la hoja de estilos:

```html
<head>
    <link rel="stylesheet" type="text/css" href="styles.css">
</head>
```

### Estilos

Le daremos estilos a las cajas:

```css
.caja {
    border: 1px solid rgb(70, 69, 69);
    background-color: white;
    color: black;
    font-family: 'Courier New', Courier, monospace;
    font-weight: bold;
    width: 120px;
    height: 120px;
    line-height: 120px;
    text-align: center;
    margin: 5px;
}
```

Anteriormente, para colocar los elementos uno al lado del otro usabamos `float: left;`, pero esto lleva más trabajo porque debemos evitar que los
elementos de abajo floten con un `.clearfix`. Pero esto es más fácil con **flexbox**.

Le daremos estilos a la clase `flex-container` del `<section>`:

```css
.flex-container {
    display: flex;
}
```

Con esto, lograremos lo mismo que con `float: left;`. Con los siguientes estilos visualizaremos mejor el `flex-container`:

```css
.flex-container {
    border: 1px solid black;
    background: #ccc;
    padding: 20px;
    display: flex;
}
```

### `flex-direction`

La layout que hagamos con flexbox va a tener siempre una dimensión: **horizontal** (como es nuestro caso actual) o **vertical**.

Ahora mismo, por defecto, esta en forma de fila, así `flex-direction: row;`. Pero también podemos usarlo en forma de columna (vertical):

```css
.flex-container {
    border: 1px solid black;
    background: #ccc;
    padding: 20px;
    display: flex;
    flex-direction: column;
}
```

También podemos usar `flex-direction: column-reverse;`, igual en forma de columna, pero del último elemento al primero. Y también podemos usar
`flex-direction: row-reverse;`, en forma de fila del último elemento al primero, pero del lado derecho. Por defecto, dejaremos `flex-direction: row;`.

Está es la facilidad que da flexbox, y aparte es un contenedor responsive en la mayoría de casos.

Ahora, si añadimos más cajas dentro del contenedor, todas van a compartir ese espacio. Incluso si añadimos un ancho y lo centramos:

```css
.flex-container {
    border: 1px solid black;
    background: #ccc;
    padding: 20px;
    display: flex;
    flex-direction: row;
    width: 80%;
    margin: 0 auto;
}
```

Seguiran amontonándose e intentando compartir ese espacio.

### `flex-wrap`

Pero si queremos tener esta layout de flexbox y no queremos que todo se quede en una fila, es decir, que cuando el contenedor se llene, continue
en una segunda fila; para eso usaremos el envoltorio de flex (`flex-wrap`), que por defecto está en `nowrap` y lo cambiaremos a
`wrap`:

```css
.flex-container {
    border: 1px solid black;
    background: #ccc;
    padding: 20px;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    width: 80%;
    margin: 0 auto;
}
```

Con esto, acomóda y organiza correctamente los elementos con un tamaño justo dentro del contenedor y se coloquen uno abajo del otro. Esto va
modificandose y organizandose en función al tamaño del contenedor.

### `flex-flow`

Existe otra propiedad que combina `flex-direction` y `flex-wrap` llamada `flex-flow`:

```css
.flex-container {
    border: 1px solid black;
    background: #ccc;
    padding: 20px;
    display: flex;
    flex-flow: row wrap;
    width: 80%;
    margin: 0 auto;
}
```

También existe `wrap-reverse`.

Eliminamos las cajas añadimos y nos quedamos con las que teníamos originalmente.

### `justify-content`

Si queremos centrar los elementos en medio del contenedor, tenemos la propiedad `justify-content`:

```css
.flex-container {
    border: 1px solid black;
    background: #ccc;
    padding: 20px;
    display: flex;
    flex-flow: row wrap;
    justify-content: space-between;
    width: 80%;
    margin: 0 auto;
}
```

Con esto ocuparán todo el espacio pero manteniendo una separación entre ellos.

Con `justify-content: space-around;`, nos va a permitir que haya el mismo espacio alrededor de los elementos.

Con `justify-content: space-evenly;`, distribuye el espaciado de forma uniforme, incluso antes del primer elemento y después del último.

Con `justify-content: center;`, centrará justo al centro del contenedor.

Con `justify-content: flex-start;`, empezarán los elementos al principio del contenedor.

Con `justify-content: end;`, empezarán al final.

Si modificamos la altura (muy grande `height: 600px`) al contenedor, si las cajas no tienen un tamaño por defecto (se lo quitamos a nuestra clase
`caja`), ocuparán toda la altura del contenedor. Se adpatarán al tamaño del contenedor, en flex, todo se adapta.

### `align-items`

Con las cajas que ocupan el toda la altura, podemos usar la propiedad `align-items` para poder centrar los elementos:

```css
.flex-container {
    border: 1px solid black;
    background: #ccc;
    padding: 20px;
    display: flex;
    flex-flow: row wrap;
    justify-content: space-between;
    align-items: flex-start;
    width: 80%;
    height: 600px;
    margin: 0 auto;
}
```

Se quedarán con la altura que tenían al principio pero arriba del contenedor. Ya no se expanden, adquieren el tamaño adecuado.

También está `center`, para tener los elementos centrados y ordenados al centro del contenedor.

También tenemos `flex-end`, para que se queden abajo del contenedor.

El que viene por defecto es el `stretch`, que expande las cajas con toda la altura del contenedor.

Lo dejaremos en `center`. Añadiremos más cajas como teníamos antes.

### `align-content`

Si quitamos el `align-items: center;`, los elementos se expanden pero ajustándose a las filas del contenedor. Si queremos ajustar los espacios
entre cada elemento y entre línea, usamos la propiedad `align-content`:

```css
.flex-container {
    border: 1px solid black;
    background: #ccc;
    padding: 20px;
    display: flex;
    flex-flow: row wrap;
    justify-content: flex-start;
    align-content: center;
    width: 80%;
    height: 600px;
    margin: 0 auto;
}
```

Esto organiza los elementos al centro.

Con `space-between`, dejaría espacio entre líneas.

Con `flex-start`, para que deje espacio filas arriba del contenedor verticalmente.

Tanto `justify-content`, `align-items`, `align-content`, tienen los mismos valores y podemos jugar con ellos como necesitemos.

Borramos las cajas que nos sobran y nos quedamos con tres. Les pondremos unas clases diferentes a cada una y les daremos estilos:

```html
<section class="flex-container">
    <div class="caja c1">
        Caja 1
    </div>
    <div class="caja c2">
        Caja 2
    </div>
    <div class="caja c3">
        Caja 3
    </div>
</section>
```

Alinearemos y justificaremos las cajas al centro. Y cambiamos el ancho de las cajas por `200px`:

```css
.flex-container {
    border: 1px solid black;
    background: #ccc;
    padding: 20px;
    display: flex;
    flex-flow: row wrap;
    justify-content: center;
    align-content: center;
    width: 80%;
    height: 600px;
    margin: 0 auto;
}

.caja {
    border: 1px solid rgb(70, 69, 69);
    background-color: white;
    color: black;
    font-family: 'Courier New', Courier, monospace;
    font-weight: bold;
    width: 200px;
    line-height: 200px;
    text-align: center;
    margin: 5px;
}
```

En flexbox, podemos ordenar las cajas selectivamente. Todo elemento dentro de un contenedor flex, tiene la posibilidad de utilizar la
propiedad `order` y colocar el orden como queramos:

```css
.c1 {
    background: lightblue;
    order: 1;
}

.c2 {
    background: lightcoral;
    order: 2;
}

.c3 {
    background: lightgreen;
    order: 3;
}
```

Las cajas se quedarán con el mismo orden. Pero podemos hacer lo siguiente:

```css
.c1 {
    background: lightblue;
    order: 3;
}

.c2 {
    background: lightcoral;
    order: 2;
}

.c3 {
    background: lightgreen;
    order: 1;
}
```

Esto hará que las cajas cambien de sitio. Sin flexbox, no podríamos hacerlo tan fácilmente.

### `flex-grow`

También tenemos la propiedad `flex-grow`, que todos los elementos hijos del contenedor de flex tienen disponible para usar.

Sirve para darle una prioridad en cuanto al ancho de ese elemento. Es decir, le podemos dar más ancho a más prioridad a ciertos elementos que
otros. Le podemos poner que `c1` ocupe un poco más de tamaño que el resto de elementos:

```css
.c1 {
    background: lightblue;
    order: 3;
    flex-grow: 5;
}

.c2 {
    background: lightcoral;
    order: 3;
    flex-grow: 1;
}

.c3 {
    background: lightgreen;
    order: 1;
    flex-grow: 1;
}
```

Los elementos que tienen el `1` se van a quedar con el mismo tamaño y el elemento que tiene el `5` va a expandirse un poco más, tiene más derecho
a expandirse.

Si le ponemos `2`, a `c2`, la caja va a expandirse y va a repartirse el espacio de la mejor manera.

Si le ponemos `5` a todos los elementos, proporcionalmente van a tener el mismo tamaño dentro del contenedor de flex. Se expanden también, pero
tienen la misma prioridad.

Con `flex-grow`, modificamos completamente el `width` que tiene cada elemento. Si le quitamos el `width` a la clase `caja`, el resultado
seguiría siendo igual.

### `flex-basis`

Relacionado con el `width`, tenemos `flex-basis`. Prácticamente, es lo mismo que poner un `witdh`:

```css
.c1 {
    background: lightblue;
    order: 2;
    flex-grow: 1;
    flex-basis: 50%;
}

.c2 {
    background: lightcoral;
    order: 3;
    flex-grow: 3;
}

.c3 {
    background: lightgreen;
    order: 1;
    flex-grow: 2;
}
```

Y ocupará un `50%` del total del contenedor flex. Obviamente, al tener el `flex-grow`, también se modifica y no va a ser un `50%` exacto porque los otros elementos tmabién comparten. Pero si pusieramos un `flex-grow: 1;` a todos los elementos:

```css
.c1 {
    background: lightblue;
    order: 2;
    flex-grow: 1;
    flex-basis: 50%;
}

.c2 {
    background: lightcoral;
    order: 3;
    flex-grow: 1;
}

.c3 {
    background: lightgreen;
    order: 1;
    flex-grow: 1;
}
```

El `50%` va a ser perfecto, de la anchura.

¿Por qué se utiliza el `flex-basis` y no el `width`? Cuando queremos combinarlo el `flex-grow` y otras propiedades de flexbox, se complementa
mucho mejor.