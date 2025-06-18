# 5. HTML - Parte 2

## Estructura (continuación)
### Atributos HTML

- **width="150px"**: Permiten ponerle un tamaño a nuestra imagen. En
este caso, 150 pixeles.

## Cargar imagen desde nuestro proyecto

Para no cargar una imagen desde internet, crearemos una carpeta dentro
del proyecto que se llame `img/` y ahí dentro guardar imágenes.

Ahora lo que hacemos es indicarle a la etiqueta `<img>` en el `src` que
nuestra imagen está dentro de la carpeta `img/` y el fichero es
`perro.jpg` (**webp** en mi caso).

## Trabajar con enlaces y páginas en un sitio web

Creamos una página nueva en la raíz del proyecto que se va a llamar
`contacto.html`.

Para cargar la página en el navegador cambiamos el `index.html` por `contacto.html`.

Pero podemos utilizar enlaces dentro de HTML para que nos lleven de una
página a otra.
Los enlaces los creamos con la etiquta `<a>`, y dentro de la etiqueta
`<a>` le ponemos el texto. Pero para que este enlace funcione le tenemos
que poner un atributo, el **href="pagina"**.
Este atributo **href=""** lo que nos va a permitir es indicar a que
página quiero que me lleve el enlace cuando hagamos clic.

## Crear tablas

Para crear una tabla usamos la etiqueta `<table>`. Le vamos a indicar un
atributo que se llama **border="1"** para que nos ponga borde en toda la
tabla.
Dentro de una tabla podemos definir las filas y las columnas.

Las filas se definen con la etiqueta `<tr>` y dentro vamos a definir columnas, con la etiqueta `<td>`.

## Formularios

Para definir un formulario usamos la etiqueta `<form>`, y dentro de esta
etiqueta creamos los diferentes elementos del fomrulario. Por ejemplo, un
elemnto muy básicos es un `<input>` de texto.
Para definimos primero una etiqueta `<label>`, y aquí debajo de la
etiqueta `<label>`, vamos a crear el `<input>` y le vamos a indicar el
atributo **type="text"** para decirle que tipo de campo queremos crear.
Hay un montón de campos pero el más común es el campo de tipo texto.

Y luego podemos crear también, por ejemplo, un elemento `<select>`. Nos permiten
meter varias opciones dentro con `<option>`. Normalmente a los
`<option>` se le suele poner el atributo **value=""** para luego que se
guarde en una base de datos o lo que sea.

Y luego, por último, podemos definir también un campo de tipo `<button>`
o de `<input type="submit" value="Enviar">` para enviar el fomrulario.
El **value** va a ser el texto que aparece en el botón del fomrulario.