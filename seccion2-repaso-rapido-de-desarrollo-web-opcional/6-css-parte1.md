# 6. CSS - Parte 1

## CSS

Hojas de Estilo en Cascada (**Cascading Style Sheets**), es un lenguaje de hojas de estilo que nos va a permitir definir y crear la presentación
de un documento de HTML.

## Ejemplo con CSS

Creamos la carpeta `aprendiendo-css/` y creamos un fichero HTML `index.html`.

### Estructura HTML

Estructura inicial del `index.html`:

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>CSS con Víctor Robles</title>
    </head>
    <body>
        <h1>CSS con Víctor Robles</h1>
    </body>
</html>
```

Creamos un `<div id="container">` con un `id`, que nos va a servir para luego seleccionar en el CSS para darle estilos:

```html
<body>
    <div id="container"></div>
</body>
```

Luego, definimos la cabecera con la etiqueta `<header>`:

```html
<body>
    <div id="container">
        <header></header>
    </div>
</body>
```

En HTML5, esta etiqueta hace referencia a la cabecera de un sitio web. De manera semántica, esta etiqueta es mejor para optimización de SEO.

Dentro del `<header>`, pondremos el título de la web:

```html
<header>
    <h1>CSS con Víctor Robles</h1>
</header>
```

Definiremos un menú con la etiqueta `<nav>`, que es otra etiqueta semántica de HTML5 que define una barra de navegación. Dentro,
definiremos una lista desordenada (`<ul>`):

```html
<nav>
    <ul>
        <li>
            <a href="index.html">
                Inicio
            </a>
        </li>
        <li>
            <a href="index.html">
                Página 1
            </a>
        </li>
        <li>
            <a href="index.html">
                Página 2
            </a>
        </li>
        <li>
            <a href="index.html">
                Blog
            </a>
        </li>
        <li>
            <a href="index.html">
                Contacto
            </a>
        </li>
    </ul>
</nav>
```

Para definir el contenido, usaremos la etiqueta `<section>` con un `id`. Dentro crearemos varios artículos con la etiqueta `<article>`, con una
clase `class="article"`. Igualmente, ambas etiquetas son mejor a nivel de SEO:

```html
<section id="content">
    <article class="article">
        <h2>Titulo del articulo</h2>
        <p>Texto del articulo</p>
    </article>
    <article class="article">
        <h2>Titulo del articulo</h2>
        <p>Texto del articulo</p>
    </article>
    <article class="article">
        <h2>Titulo del articulo</h2>
        <p>Texto del articulo</p>
    </article>
    <article class="article">
        <h2>Titulo del articulo</h2>
        <p>Texto del articulo</p>
    </article>
</section>
```

Usaremos la etiqueta `<aside>` para definir una barra lateral, ya que semánticamente representa lo mismo:

```html
<aside>
    <h2>Barra lateral</h2>
    <form>
        <input type="text">
        <input type="submit" value="Buscar">
    </form>
</aside>
```

Definimos por último el pie de página con la etiqueta `<footer>`, que semánticamente representa lo mismo:

```html
<footer>
    Víctor Robles WEB &copy; 2025
</footer>
```

### Usando CSS

#### Etiqueta `<style>`

Hay varias formas de trabajar CSS. Por ejemplo, podemos crear en el `<head>` de la página la etiqueta `<style>`:

```html
<head>
    <meta charset="utf-8">
    <title>CSS con Víctor Robles</title>
    <style></style>
</head>
```

Ahor podemos empezar a trabajar con CSS. Por ejemplo, podemos darle un background a la página usando los **selectores** para seleccionar los diferentes tipos de elemento.

Tenemos tres principales tipo se selectores:

* **De etiqueta**: Poniendo directamente el nombre de la etiqueta.
* **De id**: anteponiendo `#` mas el nombre del id.
* **De clase**: anteponiendo `.` mas el nombre de la clase.

Dentro de los selectores colocamos las reglas CSS. Por ejemplo, dentro del selector `body` colocamos la regla CSS `background`:

```html
<style>
    body{
        background: lightgray;
    }

    #container{}
    
    .article{}
</style>
```

Esto hará que la página web tenga el `background` gris suave. También podemos expresar los colores en **rgb** y en **hexadecimal**.

#### Hoja de estilos `.css`

Creamos un archivo `.css`, y pasamos los estilos dentro de este archivo:

```css
body{
    background: lightgray;
}

#container{}

.article{}
```

Y vinculamos la hoja de estilos en el `index.html`:

```html
<head>
    <link rel="stylesheet" href="estilos.css">
</head>
```

Esto es una mejor práctica, ya que separamos el HTML del CSS.

También, cambiaremos el tipo de fuente de la página web con `font-family`:

```css
body{
    background: lightgray;
    font-family: Arial, Helvetica, sans-serif;
}
```

Para tener la cabecera roja, seleccionaremos primero el `id="container"`, le pondremos un ancho con `width`, con `margin`
centraremos el elemento al centro de la página web. También le pondremos unos bordes con `border`:

```css
#container{
    /*width: 70%;*/
    width: 1100px;
    margin: 0px auto;
    border: 1px solid black;
}
```

Los comentarios en CSS se colocan con `/**/`.

Ahora, para la cabecera seleccionaremos con `header` ya que solo hay una en la página:

```css
header{
    background: red;
}
```