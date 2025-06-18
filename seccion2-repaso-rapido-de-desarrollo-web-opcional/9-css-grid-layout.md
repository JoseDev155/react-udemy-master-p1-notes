# 9. CSS Grid Layout

Es una nueva forma de maquetar en CSS, que a diferencia de flexbox, nos va a permitir hacer el layout de una web en una o varias dimensiones: tanto en horizontal como vertical, y hacer una cuadrícula que se adecue al sitio web que estamos haciendo.

## Ejemplo de Flexbox

Creamos la carpeta `repaso-grid/` y creamos dos archivos: `index.html` y `styles.css`.

### Estructura básica de HTML

Estructura del `index.html`:

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE-edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aprendiendo CSS Grid Layout</title>
</head>
<body>
    <h1>Aprendiendo CSS Grid Layout con Víctor Robles WEB</h1>

    <div class="grid-layout">
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
        <div class="caja">
            Caja 5
        </div>
        <div class="caja">
            Caja 6
        </div>
        <div class="caja">
            Caja 7
        </div>
        <div class="caja">
            Caja 8
        </div>
        <div class="caja">
            Caja 9
        </div>
        <div class="caja">
            Caja 10
        </div>
    </div>
</body>
</html>
```

Le ponemos un background al `<body>`:

```css
body {
    background-color: antiquewhite;
    font-family: Arial, Helvetica, sans-serif;
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
    width: 150px;
    height: 150px;
    border: 4px solid black;
    background-color: lightgray;
    margin: 15px;
    line-height: 150px;
    text-align: center;
}
```

Si queremos colocar todas las cajas una al lado de la otra, y cuando se llene la pantalla, que continuara en una siguiente fila de cajas.
Originalmente, lo podríamos hacer con un `float: left;`. Pero podemos optimizar esto mucho más y utilizar **grid layout**.

Con el `<div class="grid-layout">`, podemos seleccionar la clase y darle estilos, y agregar `text-align: center;` al `<body>` para centrar el
texto. Así sería originalmente:

```css
body {
    background-color: antiquewhite;
    font-family: Arial, Helvetica, sans-serif;
    text-align: center;
}

.grid-layout {
    width: 80%;
    margin: 0 auto;
}

.caja {
    width: 150px;
    height: 150px;
    border: 4px solid black;
    background-color: lightgray;
    margin: 15px;
    text-align: center;
    line-height: 150px;
    float: left;
}
```

Ahora, añadiremos otros estilos a `grid-layout`:

```css
.grid-layout {
    width: 80%;
    margin: 0 auto;
    background-color: lightgreen;
    padding: 20px;
    border: 1px solid black;
}
```

Con esto, veremos el problema de usar `float`, y es que tendríamos que limpiar los elementos que flotan abajo del `<div>`.

### grid

Así que quitamos `float` de la clase `caja`, y para usar grid layout, agregaremos al contenedor que contiene todas las cajas:

```css
.grid-layout {
    display: grid;
    width: 80%;
    margin: 0 auto;
    background-color: lightgreen;
    padding: 20px;
    border: 1px solid black;
}
```

Con esto, veremos los elementos en columnas dentro del contenedor, sin flotar.

#### `grid-template-columns`

Pero también podemos especificar cuántas columnas tendrá el layout de grid (cuadrícula):

```css
.grid-layout {
    display: grid;
    grid-template-columns: auto auto auto auto;
    width: 80%;
    margin: 0 auto;
    background-color: lightgreen;
    padding: 20px;
    border: 1px solid black;
}
```

Con esto le decimos que tenga cuatro columnas.

Ahora, haremos que las cajas ocupen todo el ancho y no tengan separación, les quitamos el `margin` y los tamaños:

```css
.caja {
    border: 4px solid black;
    background-color: lightgray;
    text-align: center;
    line-height: 150px;
}
```

Ahora las cajas estarán todas juntas.

No solo podemos indicar cuántas columnas tendrá el contenedor grid, sino el porcentaje que ocupará dentro del contenedor:

```css
.grid-layout {
    display: grid;
    grid-template-columns: 50% 20% 25%;
    width: 80%;
    margin: 0 auto;
    background-color: lightgreen;
    padding: 20px;
    border: 1px solid black;
}
```

Veremos que incluso sobra espacio dentro del contenedor.

#### `grid-template-rows`

Añadiremos más cajas (ahora irán de 1 a 12). Aparte de modificar el comportamiento de las columnas, podemos modificar el comportamiento de
las filas (la altura con respecto a la cuadrícula en general):

```css
.grid-layout {
    display: grid;
    grid-template-columns: 50% 20% 25%;
    grid-template-rows: 100px auto;
    width: 80%;
    margin: 0 auto;
    background-color: lightgreen;
    padding: 20px;
    border: 1px solid black;
}
```

#### `justify-content`

Nos va a permitir ajustar o alinear nuestro contenido:

```css
.grid-layout {
    display: grid;
    grid-template-columns: 50% 20% auto;
    grid-template-rows: 100px auto;
    justify-content: flex-start;
    width: 80%;
    margin: 0 auto;
    background-color: lightgreen;
    padding: 20px;
    border: 1px solid black;
}
```

Esto colocará los elementos al princicio del contenedor de grid. Las filas y columnas que tienen `auto` se van adaptar al espacio que tengan.

Con `flex-end` se colocan al final.

Con `center` se colocan al centro.

Con `space-around` se colocan con espacio entre cada columna.

Con `space-between` se colocan con espacio entre cada columna pero pegando la columna del principio y del final a los lados.

Lo dejaremos en `stretch` para que se quede por defecto, ocupando todo el espacio.

### Características en hijos de grid layout

Ahora, iremos al HTML y le pondremos una clase exclusiva a cada una de las cajas: `c1, c2, ..., c12`. Ahora, veremos que características de CSS
grid tenemos para elementos individuales hijos de grid layout, dentro del `<div class="grid-layout">` principal.

### `grid-column`

Vamos a seleccionar `c1`. `grid-column` nos permite indicarle cuántas columnas queremos que ocupe el elemento `c1` dentro del grid.

Si nos vamos a las **Herramientas de desarrollador** en el navegador, nos vamos a **Inspeccionar** y marcamos **Superponer rejilla**, veremos
las líneas verticales y horizontales del grid. Es importante tenerlo en cuenta a la hora de maquetar con grid para poder expandir los elementos.

También pondremos en `auto` todas las columnas y filas de `grid-layout`. Si queremos que la **Caja 1** ocupe todas las columnas, haremos que vaya
desde la línea `1` hasta la `4`:

```css
.grid-layout {
    display: grid;
    grid-template-columns: auto auto auto;
    grid-template-rows: auto;
    justify-content: stretch;
    width: 80%;
    margin: 0 auto;
    background-color: lightgreen;
    padding: 20px;
    border: 1px solid black;
}

.c1 {
    grid-column: 1/4;
    background-color: lightskyblue;
}
```

Veremos que la **Caja 1** se expande completamente y el resto de elementos del grid, se recolocan cómo sea conveniente.

Para que **Caja 2** ocupe desde la línea `1` hasta la `3`:

```css
.c2 {
    grid-column: 1/3;
    background-color: lightyellow;
}
```

Veremos que ocupa otro espacio, y se recolocan los demás elementos.

Le daremos estilos a `c3` y `c12`. Y expandimos la **Caja 11** para llenar el hueco dejado por `c12`:

```css
.c3 {
    grid-column: 3/4;
    background-color: lightsalmon;
}

.c11{
    grid-column: 2/4;
}

.c12 {
    grid-column: 1/4;
    background-color: lightseagreen;
}
```

Queda mejor la cuadrícula.

Otra forma de indicarle a grid cuántas columnas puede ocupar un elemento, es indicándole que se "expanda 3 columnas":

```css
.c12 {
    grid-column: 1 / span 3;
    background-color: lightseagreen;
}
```

El resultado seguirá siendo el mismo.

### `grid-row`

Quitamos todos los `grid-column` y aprenderémos a utilizar la propiedad `grid-row.` Que es igual a la anterior, pero para expandir los elementos a nivel de fila.

Haremos que la **Caja 1** ocupe 2 filas:

```css
.c1 {
    grid-row: 1 / span 2;
    background-color: lightskyblue;
}
```

### `grid-area`

Quitamos todos los `grid-row` y usaremos `grid-area`, e indicaremos que **Caja 1** empiece en la línea de la fila `1`, que se expanda hasta la
línea `3`, que empiece en la línea `1` a nivel de columna hasta la línea `4` a nivel de columna:

```css
.c1 {
    grid-area: 1 / 1 / 3 / 4;
    background-color: lightskyblue;
}
```

### Ejemplo con `grid-column`

Y quitamos cajas extras y las dejamos de la siguiente manera:

```html
<div class="grid-layout">
    <div class="caja c1">
        CABECERA
    </div>
    <div class="caja c2">
        MENU
    </div>
    <div class="caja c3">
        CONTENIDO
    </div>
    <div class="caja c4">
        BARRA LATERAL
    </div>
    <div class="caja c5">
        PIE PÁGINA
    </div>
</div>
```

Modificaremos `grid-layout`, y tendremos solo 2 columnas, 1 para la **BARRA LATERAL**, otra para el **CONTENIDO**. Filas serán automáticas
por lo cual quitaremos `grid-template-rows` y `justify-content`. También quitaremos `width`, `margin` y `padding`. Tmabién quitaremos `grid-area`
de `c1` para hacer todo desde el comienzo:

```css
.grid-layout {
    display: grid;
    grid-template-columns: auto auto;
    background-color: lightgreen;
    border: 1px solid black;
}

.c1 {
    background-color: lightskyblue;
}
```

Para que `c1` ocupe 2 columnas, agregamos `grid-column`. También le daremos un tamaño a cada fila, y para que esto funcione le vamos a poner una altura a `grid-layout`:

```css
.grid-layout {
    height: 650px;
    display: grid;
    grid-template-columns: auto auto;
    grid-template-rows: 20% 10% 60% auto;
    background-color: lightgreen;
    border: 1px solid black;
}

.c1 {
    grid-column: 1 / span 2;
    background-color: lightskyblue;
}
```

Para `c2` que sería el **MENU**:

```css
.c2 {
    grid-column: 1 / span 2;
    background-color: lightyellow;
}
```

Quitamos `line-height` a la clase `caja` y le ponemos un `padding`:

```css
.caja {
    border: 4px solid black;
    background-color: lightgray;
    text-align: center;
    padding: 20px;
}
```

Luego al **PIE PÁGINA**, que es el último elemento (`c5`):

```css
.c5 {
    grid-column: 1 / span 2;
    background-color: lightpink;
}
```

Veremos que el **CONTENIDO** y la **BARRA LATERAL** comparten el mismo espacio. Para hacer que la **BARRA LATERAL** tenga menos espacio y  el
**CONTENIDO** tenga mas a nivel de ancho, de columna, modificaremos el tamaño de las columnas que tenemos en grid.

Es decir, tenemos dos columnas en el `grid-template-columns: auto auto;`, entonces:

```css
.grid-layout {
    height: 650px;
    display: grid;
    grid-template-columns: 80% auto;
    grid-template-rows: 20% 10% 60% auto;
    background-color: lightgreen;
    border: 1px solid black;
}
```

Esto hará que la primera sea mas ancha y la otra mas estrecha.

### `grid-template-areas`

Quitamos `grid-template-columns` y `grid-template-rows` de la clase `grid-layout`, y todos los estilos de grid a `c1, c2, ..., c5`:

```css
.grid-layout {
    height: 650px;
    display: grid;
    background-color: lightgreen;
    border: 1px solid black;
}

.c1 {
    background-color: lightskyblue;
}

.c2 {
    background-color: lightyellow;
}

.c3 {
    background-color: lightsalmon;
}

.c4{
    background-color: rgb(104, 77, 66);
}

.c5 {
    background-color: lightpink;
}
```

Usaremos el `grid-template-areas`, con esto podemos indicar que elementos queremos que ocupen cada fila.

Podemos decirle que haya 2 columnas, entonces, la primera fila que la ocupe la cabecera. La segunda, el menú. La tercera, el contenido y el lateral. Y la última fila que tenga el footer:

```css
.grid-layout {
    height: 650px;
    display: grid;
    grid-template-areas: 'cabecera cabecera'
    'menu menu'
    'contenido lateral'
    'footer footer';
    background-color: lightgreen;
    border: 1px solid black;
}
```

Como hay 2 columnas, queremos que se distribuya de esa manera.

Ahora mismo, esto no va a funcionar. Para que esto funcione, le tenemos que indicar a cada elemento a que área pertenece:

```css
.c1 {
    grid-area: cabecera;
    background-color: lightskyblue;
}

.c2 {
    grid-area: menu;
    background-color: lightyellow;
}

.c3 {
    grid-area: contenido;
    background-color: lightsalmon;
}

.c4{
    grid-area: lateral;
    background-color: rgb(104, 77, 66);
}

.c5 {
    grid-area: footer;
    background-color: lightpink;
}
```

Y se van a expandir todas las veces que aparezcan en `grid-template-areas`.

Ahora, podemos modificar el tamaño con `grid-template-rows` y `grid-template-columns`:

```css
.grid-layout {
    height: 650px;
    display: grid;
    grid-template-areas: 'cabecera cabecera'
    'menu menu'
    'contenido lateral'
    'footer footer';
    grid-template-rows: 20% 10% auto 10%;
    background-color: lightgreen;
    border: 1px solid black;
}
```

Y las cajas se ajustan correctamente.

Estas son las ventajas de CSS Grid Layout, podemos manipular la estructura de un sitio web, y todo esto es responsive. Todo esto se
puedde combinar con `float`'s, on flexbox, etc.