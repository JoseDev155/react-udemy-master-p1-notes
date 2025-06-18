# 12. JavaScript básico general

## Ejemplo de JavaScript

Creamos la carpeta `RepasoJS/` y creamos el archivo `index.html`. Para poder trabajar con JavaScript, debemos tener un archivo HTML en el cual
cargar ese JavaScript.

### Estructura básica de HTML

Estructura del `index.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Repaso JavaScript</title>
</head>
<body>
    <h1>
        Aprendiendo JavaScript rápido
    </h1>
    <p>Hola soy Víctor Robles WEB</p>
</body>
</html>
```

### Uso de JavaScript y función `alert()`

#### Forma 1

Para empezar a trabajar con JavScript, lo podemos hacer mediante la etiqueta `<script>`:

```html
<head>
    <meta charset="UTF-8">
    <title>Repaso JavaScript</title>
    <script>
        alert('hola mundo!!')
    </script>
</head>
```

Esto sacará una ventana emergente en nuestro navegador y así mostrar una alerta.

#### Forma 2

La forma más óptima es crear un archivo `main.js`. Y poner el código en ese archivo:

```javascript
alert('hola mundo!!')
```

Y lo cargamos en el `<head>` de la web e indicarle que esta etiqueta va a cargar un texto de tipo JavaScript:

```html
<head>
    <meta charset="UTF-8">
    <title>Repaso JavaScript</title>
    <script src="main.js" type="text/javascript"></script>
</head>
```

### Variables

Son como una caja donde guardamos información. En este caso usaremos la palabra reservada `var` para definir una variable:

```javascript
var nombre = "Víctor Robles"; // string
var altura = 190;             // number
```

Para mostrarlo por pantalla en JavaScript:

```javascript
document.write(nombre);
document.write(nombre);
```

De esta manera, incluiremos la variable dentro del HTML. Pero apareceran pegados, para evitar esto, concatenaremos ambas variables:

```javascript
var concatenacion = nombre + " " + altura;

document.write(concatenacion);
```

Pero usar `document.write()` es muy poco óptimo.

### `document.getElementById()`

Una forma más usada es mediante id's:

```html
<div id="datos"></div>
```

Y dentro, imprimiremos lo que queramos. Ahora, seleccionamos el id:

```javascript
var datos = document.getElementById("datos");
datos.innerHTML = concatenacion;
```

Con `innerHTML`, añadimos lo que queramos. Pero, ya que el `<script>` se jecuta antes, intenta leer el id en `<div id="datos">` cuando todavía no existe, por ende no se carga el contenido en pantalla.

Para eso, llevamos la etiqueta `<script>` al final del `<body>`:

```html
<body>
    <!-- HTML -->
    
    <script src="main.js" type="text/javascript"><script>
</body>
```

De esta manera, si se añade el contenido a nuestro `<div id="datos">`.

### Template strings

También, podemos usar lo que se conoce como **template strings** de JavaScript. Usando las comillas invertidas, podemos incluir HTML. Además,
con `${}` podemos concatenar variables:

```javascript
var datos = document.getElementById("datos");
datos.innerHTML = `
    <h1>Soy la caja de datos</>
    <h2>Mi nombre es: ${nombre}</h2>
    <h3>Mido: ${altura} cm</h3>
`;
```

Así podemos hacer plantillas para ir utilizandolas dentro de variables e ir montándolas en una vista.

Hemos metido este HTML, **template string**, con **variables interpoladas**, es decir, mostrando una variable dentro de un string, dentro de código HTML dinámicamente.

### Estructuras de control

#### Condicional `if`

Ejemplo sin **template strings**:

```javascript
var altura = 189;

if (altura >= 190) {
    datos.innerHTML += '<h1>Eres una persona ALTA</h1>';
} else {
    datos.innerHTML = '<h1>Eres una persona BAJITA</h1>';
}
```

Para evitar que `innerHTML` nos elimine todo el contenido HTML que asignamos anteriormente, utilizamos el operador `+=`, que es un operador
de asignación que recoge el valor original de `datos` y agrega/suma el nuevo HTML que estamos asignando.

#### Bucles

Sirven para repetir un grupo de instrucciones, mientras que una condición se cumpla.

##### Bucle `for`

Lo primero que indicamos es el inicializador, el segundo parámetro que recibe el bucle `for` es la condición y el tercer parámetro es el
incrementador. De esta manera, dentro de las llaves se va a estar ejecutando un bloque de instrucciones hasta que la condición deje de
cumplirse:

```javascript
for (var i = 2000; i <= 2020; i++) {
    // bloque de instrucciones
    datos.innerHTML += "<h2>Estamos en el año: " + i + "</h2>";
}
```

Con esto mostraremos todos los años desde el 2000 hasta el 2020, es una estructura iterativa.

#### Comentarios

Son trozos de código que no se ejecutan. Se pueden hacer con `/**/` o `//`.

#### Funciones

Se definen con la palabra reservada `function`. Podemos ejecutar un bloque de instrucciones dentro de ellas.

Comentamos desde la variable `concatenacion` hasta el bucle `for`.

Tomamos el siguiente código y lo pegamos dentro de la función, para que solo se ejecute ahí. También podemos pasarle **parámetros** a las
funciones, para abstraer la lógica que hay adentro de ella y que no sea fija para un caso concreto:

```javascript
function MuestraMiNombre(nombre, altura) {
    var datos = document.getElementById("datos");
    datos.innerHTML = `
        <h1>Soy la caja de datos</>
        <h2>Mi nombre es: ${nombre}</h2>
        <h3>Mido: ${altura}</h3>
    `;
}
```

En lugar de usar las variables globales `nombre, altura`, usará las variables locales que declaramos como parámetros.

Ahora, invocamos la función:

```javascript
MuestraMiNombre("Víctor Robles WEB", 190);
```

Esto es totalmente variable. Si cambiamos algo, lo imprime también:

```javascript
MuestraMiNombre("Víctor Robles WEB 111", 190);
```

Podríamos hacer una función que solamente nos imprima los datos:

```javascript
function MuestraMiNombre(nombre, altura) {
    var misDatos = `
        <h1>Soy la caja de datos</>
        <h2>Mi nombre es: ${nombre}</h2>
        <h3>Mido: ${altura}</h3>
    `;

    return misDatos;
}
```

Al devolver la variable, sacamos fuera de la función unos datos. Cuando invoquemos la función, devolverá la variable:

```javascript
function imprimir() {
    var datos = document.getElementById("datos");
    datos.innerHTML = MuestraMiNombre("Víctor Robles WEB 111", 190);
}

imprimir();
```

Esto imprimirá los mismos datos por pantalla. Y si queremos modificar algo, lo hacemos en la invocación:

```javascript
datos.innerHTML = MuestraMiNombre("Víctor Robles WEB", 190);
```

#### Arrays

Son variables con múltiples valores o **colección de datos**. Se definen con los corchetes `[]`:

```javascript
var nombres = ['Víctor', 'Antonio', 'Joaquin'];
```

Los arrarys empiezan por `0` y accedemos a sus valores mediante corchetes `[]`. Mostraremos sus valores con un `alert()`:

```javascript
alert(nombres[1]);
```

También podemos recorrer los arrays:

```javascript
document.write('<h1>Listado de nombres</h1>');
for (i = 0; i < nombres.length; i++) {
    document.write(nombres[i] + '<br />');
}
```

El `.length` cuenta el número de elementos en un array (p longitud). Con este bucle, mostraremos los nombres.

### `.forEach` y callback

También podríamos recorrelo con `.forEach()` y pasrle una función de `callback`. Una función de `callback` es una función que se ejecuta
dentro de otra. Además, es una función que no tiene nombre, es **anónima**.

En cada iteración del bucle, vamos a crear un objeto:

```javascript
nombres.forEach(function (nombre) {
    document.write(nombre + '<br />');
});
```

### Funciones flecha

Podemos definir funciones anónimas o de callback como una **función flecha**:

```javascript
nombres.forEach((nombre) => {
    document.write(nombre + '<br />');
});
```