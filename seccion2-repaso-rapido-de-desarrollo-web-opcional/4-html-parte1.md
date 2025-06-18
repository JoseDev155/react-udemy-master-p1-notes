# 4. HTML - Parte 1

## HTML

**HTML (HyperText Markup Language)** es un lenguaje de marcado que nos
va a permitir darle la estructura básica a una página
web, darle un contenido a esa página web a nivel de texto, imágenes, video, etc.

Para aprender HTML crearemos una carpeta llamada `aprendiendo-html/` y la abrimos en Visual Studio Code.

Las páginas web que creemos deben tener la extensión .html y crearemos la página **index.html** (típicamente se le llama así a la página
principal de un sitio web)

## Estructura

- `<!DOCTYPE html>`: Versión de HTML a usar (última versión)
- `<html></html>`: Contiene todo el sitio web.
- **Etiqueta**: Algo que se abre y cierra `<> </>`. Hay un montón de
etiquetas y cada una de la etiquetas nos va a permitir crear un tipo de elemento dentro de la página web. Hay para párrafos, para cajas, para
imágenes, para tablas, para listas, para lo que sea.
- `<head></head>`: Contiene los metadatos, datos que le interesan al
navegador pero el usuario no los va a ver como tal.
- `<meta charset="utf-8">`: Para que HTML reconozca los textos en español.
- `<title></title>`: Título de la página web.
- `<body></body>`: Todo o que verá el usuario en el cuerpo de la página web.
- `<h1></h1>`: Permite definir el encabezado de una página web.
- `<h2></h2>`: Encabezado de segundo nivel. Hay varios tipos de
encabezado, van del 1-5.
- `<p></p>`: Párrafo, en diferentes líneas. Si colocamos el texto sin
estas etiquetas, se pegaran un al lado del otro.
- `<br/>`: Salto de línea. es una etiqueta que no se abre y se cierra
como las que tienen contenido, sino que es una etiqueta que hace una
funcionalidad que es el salto de línea. Y para cerrar las etiquetas que
no tienen contenido, pues se le pone el barra por aquí o la diagonal
por aquí.
- `<hr>`: Líneas separadora
- `<ul></ul>`: Lista desordenada (con puntos en lugar de números).
- `<li></li>`: Elemento de una lista.
- `<ol></ol>`: Lista ordenada por números
- `<img></img>`: Sirve para insertar imágenes. Con los atributos
le damos valores extra a esa etiqueta. Como esta etiqueta no tiene
contenido de texto podemos cerrarla así: `<img alt="" src="" />`.
Atributos:
    - **alt="texto"**: Texto alternativo en el caso de que no se cambie
    la imagen.
    - **src="imagen"**: Indicamos a la etiqueta que imagen va a cargar.