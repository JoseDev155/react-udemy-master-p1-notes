# 7. CSS - Parte 2

## Continuación

Al `header`, también le daremos una altura y un ancho:

```css
header{
    background: red;
    height: 100px;
    width: 100%;
}
```

También, al `<h1>` le quitaremos los márgenes. Usaremos `*` para seleccionar todos los ementos en el navegador:

```css
*{
    margin: 0px;
    padding: 0px;
}
```

El `padding` es el margen interior dentro de una caja. Si creamos más elementos `header`, se le van a aplicar los mismos estilos.

Los id no se pueden repetir.

Centramos el texto horizontal y verticalmente:

```css
header{
    background: red;
    height: 100px;
    width: 100%;
    margin: 0px;
    text-align: center;
    line-height: 100px;
    color: white;
}
```

`line-height` y `height`, valen lo mismo, ya que es la altura que tiene la caja, asi la línea queda en medio. Y ponemos un color al texto.

También le ponemos un borde por abajo, para separarlo de cualquier otro elemento:

```css
header{
    background: red;
    height: 100px;
    width: 100%;
    margin: 0px;
    text-align: center;
    line-height: 100px;
    color: white;
    border-bottom: 3px dashed black;
}
```

`dashed` es un borde punteado.

Ahora, con el menú, seleccionamos la `<nav>` y los elementos dentro de ella, como el `<ul>` y el `<li>`. Los `<li>` los colocamos uno al lado
del otro.

Con `float: left;` haremos que cada uno de los elementos se floten a la izquierda y se pongan al lado del otro. También vamos a separar cada uno
de los elementos y le vamos a quitar los estilos por defecto con `list-style: none;`.

Le pondremos un margin a todos los elementos para que se separen un poco:

```css
nav ul li{
    float: left;
    list-style: none;
    margin: 10px;
}
```

También haremos que los elementos de abajo no suban hacia arriba,
creando un `<div>` entre el `<nav>` y el `<section>`:


```html
<nav></nav>

<div class="clearfix"></div>

<section class="content"></section>
```

Así, le daremos estilos a la clase `clearfix`:

```css
.clearfix{
    clear: both;
}
```

Estos para que cuando flotamos los elementos, los elementos de abajo se queden en su sitio.

Le daremos un background, una altura y un borde por debajo al `<nav>`:

```css
nav{
    background: lightblue;
    height: 50px;
    border-bottom: 1px solid black;
}
```

Y centraremos los enlaces con `line-height`:

```css
nav ul li{
    float: left;
    list-style: none;
    margin: 10px;
    line-height: 30px;
}
```

Para el contenido, seleccionamos el `id="content"` y le pondremos estilos. `float: left;` para que flote a la izquierda (y tambien se la
pondremos a la etiqueta `<aside>`), tambien le pondremos una anchura del `80%` y un background.

A la etiqueta `<aside>` le pondremos una anchura del `20%` para que ocupe ese espacio restante y un background:

```css
#content{
    float: left;
    width: 80%;
    background: green;
}

aside{
    float: left;
    width: 20%;
    background: orange;
}
```

Ahora, el `<footer>` se sube hacia arriba. Para evitarlo, copiamos y pegamos el `<div>` con la clase `clearfix` en medio de las etiquetas
`<nav>` y `<footer>`:

```html
<aside></aside>

<div class="clearfix"></div>

<footer></footer>
```

También le daremos una altura mínima, tanto al `content` como al `<aside>`:

```css
#content{
    float: left;
    width: 80%;
    background: green;
    min-height: 500px;
}

aside{
    float: left;
    width: 20%;
    background: orange;
    min-height: 500px;
}
```

Ahora, le daremos estilos al `<footer>`:

```css
footer{
    background: black;
    color: white;
    text-align: center;
    height: 50px;
    line-height: 50px;
}
```

## Márgenes

Podemos poner márgenes por fuera y por dentro. Por ejemplo, en la barra lateral separaremos el contenido que tiene dentro de los bordes.

Para ello, usaremos `padding` en los estilos de `<aside>`, pero esto hará que la etiqueta se salga de su posición. Para no tener este error,
usaremos la función `calc()` en el ancho. Le quitaremos `10px` de la izquierda y de la derecha, osea, `20px`:

```css
aside{
    float: left;
    width: calc(20% - 20px);
    background: orange;
    min-height: 500px;
    padding-left: 10px;
    padding-right: 10px;
    padding-top: 20px;
}
```

`padding` sirve para dar márgenes interiores.

Le daremos un `padding` general al contenido:

```css
#content{
    float: left;
    width: calc(80% - 80px);
    background: green;
    min-height: 500px;
    padding: 40px;
}
```

Le daremos estilos artículos. Le cambiaremos el color al texto, `margin` por arriba y por abajo, un borde por debajo y un padding por debajo.

También seleccionaremos el primer artículo y le pondremos un borde por arriba y un `padding` por arriba.

También modificaremos el tamaño de los `<h2>` dentro de los artículos:


```css
.article{
    color: white;
    margin-top: 15px;
    margin-bottom: 15px;
    padding-bottom: 10px;
    border-bottom: 1px solid #eee;
}

.article:first-child{
    padding-top: 10px;
    border-top: 1px solid #eee;
}

.article h2{
    font-size: 25px;
}
```