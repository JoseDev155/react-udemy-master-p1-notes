# 13. Objetos

Una cosa muy importante en JavScript que usaremos mucho son los **objetos JSON** o los **objetos literales**.

## Crear un objeto JSON

Declaramos una variable y usamos las llaves `{}`. Y le vamos indicando las propiedades:

```javascript
var coche = {
    modelo: 'Mercedes Clase A',
    maxima: 500,
    antiguedad: 2020
};
```

Y ya creamos nuestro objeto literalmente. Para mostrar los datos de ese objeto, haremos:

```javascript
document.write("<h1>" + coche.modelo + "</h1>");
```

Accedemos a las propiedades del objeto mediante `.` y el nombre de la propiedad. Esto nos mostrará el `modelo`.

## Crear funciones o métodos dentro del objeto

Ejemplo:

```javascript
var coche = {
    modelo: 'Mercedes Clase A',
    maxima: 500,
    antiguedad: 2020,
    mostrarDatos() {
        coonsole.log(modelo, maxima, antiguedad);
    },
    propiedad1: "valor aleatorio"
};
```

Este dato se mostrará dentro de la consola del navegador. Para invocar este método, accedemos al objeto, y luego, accedemos al método:

```javascript
coche.mostrarDatos();
```

Pero obtendremos un error `Uncaught ReferenceError: modelo is not defined`. Ya que deberían ser variables que tendríamos dentro del método.

Para acceder a las propiedades del objeto, debemos usar el operador `this`, que nos ayuda a acceder a las propiedades del objeto:

```javascript
var coche = {
    modelo: 'Mercedes Clase A',
    maxima: 500,
    antiguedad: 2020,
    mostrarDatos() {
        coonsole.log(this.modelo, this.maxima, this.antiguedad);
    },
    propiedad1: "valor aleatorio"
};
```

Ahora si se mostrarán los datos del objeto. Podemos incluir estructuras de control y toda la lógica que queramos a estos métodos.

Así podemops crear objetos literales. Los JSOn lo usaremos para respuestas de la API, enviar datos, etc.

También podemos hacer:

```javascript
console.log(coche);
```

Y nos mostrará su contenido.