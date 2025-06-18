# 10. SASS

## ¿Qué es SASS?

**SASS** es un **preprocesador CSS**.

Un preprocesador CSS, es una tecnología que dota a CSS de capacidades de un lenguaje de programación. Es decir, lo dota de variables, funciones, anidación, etc.

## Instalar SASS

Vamos a su [web oficial](https://sass-lang.com/install). Lo instalaremos vía **Node.js** con **npm**, por lo cual debemos tenerlo instalado.

Para instalarlo de manera global, escribimos en la consola:

```bash
npm install -g sass
```

Podemos comprobar la instalación y la versión de SASS, escribiendo en la consola:

```bash
sass --version
```

## Ejemplo de SASS

Creamos la carpeta `repaso-sass/` y creamos dos archivos: `index.html` y `styles.sass` o `styles.scss` (las dos extensiones funcionan).

Todo lo que hagamos con SASS, no lo podemos incluir directamente en nuestra página web como lo hacíamos con CSS. Tenemos que compilarlo primero, o **transpilarlo** mejor dicho, para convertirlo a un fichero de estilos de CSS.

### Estructura básica de HTML

Estructura del `index.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE-edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aprendiendo SASS</title>
</head>
<body>
    <h1>Aprendiendo SASS con Víctor Robles</h1>

    <div>
        <p>Hola</p>
    </div>

    <div>
        <p>Hola 2</p>
    </div>
</body>
</html>
```

### Instalar extensión de SASS

**Sass** para VSCode de **Syler**.


### Uso de SASS

Estilos al `body`:

```scss
body {
    background: #ccc;
}
```

Si tratamos de cargar nuestra hoja de estilos de SASS, no va a funcionar:

```html
<link rel="stylesheet" type="text/css" href="styles.sass">
```

Y si funciona, no es lo correcto cargarlo de esta forma. Lo correcto es cargar una hoja de estilos CSS. Esto lo hacemos compilando nuestro
código.

#### Compilar SASS

Para compilar nuestro código, nos aseguramos de estar dentro de la carpeta de nuestro proyecto, abrimos una terminal y escribimos:

```bash
sass --watch entrada salida
```

* `--watch`: Esto revisa los cambios guardados en el fichero de SASS y lo vuelve a compilar automáticamente.
* `entrada`: El nombre de nuestro fichero de SASS.
* `salida`: El nombre que tendrá el fichero de estilos CSS de salida.

Entonces, escribimos:

```bash
sass --watch styles.sass styles.css
```

Esto mnos dará un error, ya que SASS tiene dos formas de trabajar:

* **Sintaxis indentada**: La cual no utiliza llaves. Esto solo pasa en los ficheros `.sass`.

* **Sintaxis CSS**: La cual es parecida a CSS. Esto solo pasa en los ficheros `.scss`.

Entonces, cambiamos la extensión a `.scss` de nuesto fichero de SASS, y ejecutamos:

```bash
sass --watch styles.scss styles.css
```

Esto generará dos ficheros:

```plaintext
styles.css
styles.css.map
```

Al fichero `.map`, no le daremos importancia. Pero al otro, veremos que todo lo que hemos escrito en el fichero SASS, lo ha convertido a CSS.

Ahora, cargamos el fichero CSS:

```html
<link rel="stylesheet" type="text/css" href="styles.css">
```

#### Comentarios

Usando `//`, como en otros lenguajes de programación.

#### Variables

SASS nos permite crear variables:

```scss
$color-principal: #ccc;
$color-letra: green;

body {
    background: $color-principal;
}

h1 {
    color: $color-letra;
}

p {
    color: $color-letra;
}
```

Así, podemos reutilizar la variable las veces que necesitemos en nuestro proyecto. Cuando se transpila a CSS, se sustituyen las variables por los
colores dentro de las variables:

```css
body {
  background: #ccc;
}

h1 {
  color: green;
}

p {
  color: green;
}
```

#### Anidación

Si vemos nuestro HTML, tenemos 2 `<div>`'s con párrafos dentro. Podríamos crear un selector, agregando una clase:

```html
<div class="caja">
    <h2>Encabezado</h2>
    <p>Hola</p>
</div>

<div class="caja">
    <h2>Encabezado</h2>
    <p>Hola 2</p>
</div>
```

Le damos estilos a los párrafos y al `<h2>` que hay dentro de la `caja`. Con CSS normal, lo haríamos así:

```css
.caja p {
}

.caja h2 {
}
```

Y aquí poner sus correspondientes propiedades CSS.

En SASS, usaríamos la anidación. Tenemos la regla `caja`, y dentro podemos anidadr otras reglas:

```scss
.caja {
    h2 {
        color: black;
        font-family: Arial;
    }

    p {
        font-family: Verdana, Geneva, Tahoma, sans-serif;
        text-decoration: underline;
    }
}
```

Veremos como se aplican los estilos a los elementos HTML. A nivel de CSS, se traduce a este código:

```css
.caja h2 {
  color: black;
  font-family: Arial;
}
.caja p {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  text-decoration: underline;
}
```

#### Anidación en otro fichero CSS

Creamos el fichero `anidacion.scss`, y agregamos el código anterior de la anidación en `styles.scss` dentro de este nuevo fichero.

Podemos hacer uso de **partials** y módulos, es decir, podemos incluir otro fichero dentro de un fichero de SASS. Podemos tener muchos ficheros
de SASS incluidos en uno principal, a esto le podríamos llamar módulo.

Para que esto funcione y que siga los estándares, debemos renombrar el fichero que creamos a `_anidacion.scss`.
Para cargar el fichero dentro de `styles.scss`, lo cargamos al principio del fichero:

```scss
@use 'anidacion';
```

Veremos que seguirán funcionando los estilos.

#### Mixins

Son como funciones:

```scss
$color-letra: blue;

@mixin caja_personalizada($fondo: white) {
    background-color: $fondo;
    border: 4px solid black;
    box-shadow: 0px 0px 2px black;
    color: $color-letra;
    margin: 20px;
}
```

Ahora mismo no veremos ningún cambio salvo el color de `$color-letra`. Pero si cargamos los estilos dentro de la clase:

```scss
.caja {
    @include caja_personalizada();
}
```

Si queremos cambiarle algún valor, podemos pasárselo por parámetro:

```scss
.caja {
    @include caja_personalizada($fondo: yellow);
}
```

Veremos que se aplican los estilos.

Si tuviéramos mas cajas con otras clases diferentes:

```html
<div class="caja">
    <h2>Encabezado</h2>
    <p>Hola</p>
</div>

<div class="caja-secundaria">
    <h2>Encabezado</h2>
    <p>Hola 2</p>
</div>

<div class="caja-secundaria">
    <h2>Encabezado</h2>
    <p>Hola 2</p>
</div>
```

Podemos reutilizar el mixin la clase `caja-secundaria`:

```scss
.caja {
    @include caja_personalizada();
}

.caja-secundaria {
    @include caja_personalizada();
}
```

Veremos que los `<div>`'s que usan la clase `caja`, utilizan el color de letra del módulo `_anidacion.scss` y no el del mixin para el `<h2>`.
Mientras que `caja-secundaria` utiliza lo que hemos puesto dentro del mixin.

También podemos pasarle parámetros al mixin y cambiarle el fondo:

```scss
.caja-secundaria {
    @include caja_personalizada($fondo: gray);
}
```

Y podemos hacer varias variantes. Podemos hacer que el color por defecto sea `$color-letra`. Y luego cambiarlo en `caja-secundaria`:

```scss
@mixin caja_personalizada($fondo: white, $color: $color-letra) {
    background-color: $fondo;
    border: 4px solid black;
    box-shadow: 0px 0px 2px black;
    color: $color;
    margin: 20px;
}

.caja-secundaria {
    @include caja_personalizada($fondo: gray, $color: red);
}
```

Aunque no sobreescribe los estilos de los párrafos, ya que tienen mas prioridad.

#### Operadores

Nos permiten hacer operaciones matemáticas dentro de nuestra hoja de estilos.

En CSS, a menos que usemos la función `calc()`, no podemos hacer ningún tipo de operación. En SASS, si podemos.

Si queremos cambiar las medidas que tienen nuestras cajas (podemos manipular `caja` y `caja-secundaria` en la misma regla), entonces,
podemos hacer:

```scss
.caja, .caja-secundaria {
    width: 400px + 100px;
}
```

Esto hace la operación matemática sin ningún problema. Si Inspeccionamos el elemento con las **Herramientas de desarrollador**, veremos que tiene
`500px`. También podemos hacer operaciones de multiplicación y división.

Todo esto es solo una parte de lo que podemos hacer con SASS.