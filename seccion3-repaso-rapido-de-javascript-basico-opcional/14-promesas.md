# 14. Promesas

Son estructuras, es un objeto, que es muy usado sobre todo en peticiones asíncronas. Cuando hacemos peticiones `ajax` o cuando hacemos peticiones
que pueden tardar un tiempo en devolver un resultado (o puede no devolver nada).

Hay muchas librerías, muchas cosas internas y funcionalidades de JavaScript que utilizan promesas.

Una **promesa** representa un valor que puede estar disponible ahora, en el futuro o nunca. Vamos a poder capturar la respuesta positiva de un
servicio, de un trozo de código, de una petición `ajax`, o la parte en que esa petición es rechazada, o cuando no nos llegan esos datos, y vamos
a controlar muy bien el código.

La promesa nos promete que nos va a llegar un dato o nos va a llegar un error, y vamos a poder sacar ese dato de manera asíncrona cuando nos llegue la respuesta.

## Ejemplo de promesa

Creamos un objeto de tipo `Promise()` que recibe una función de `callback` que recibe o una `resolve` o una `reject`. Es decir, recibe el
dato positivo que resuelve la promesa o que no ha resuelto la promesa.

Aquí simulamos un llamado asíncrono con la función `setTimeout()` que también recibe una función de `callback`, y lo que hace es esperar unos
segundos a que algo se ejecute. Los segundos los expresamos en milisegundos.

La diferencia entre `let` y `var` es el alcance de esa variable dentro de un trozo de código.

Comprobamos si el saludo existe, haremos un `resolve()` y le pasamos `saludo` para mostrarlo luego. Y si no, usamos la función `reject()`:

```javascript
var saludar = new Promise((resolve, reject) => {
    setTimeout(() => {
        let saludo = "Hola muy buenas a todos chavales!!!";

        if (saludo) {
            resolve(saludo);
        } else {
            reject('No hay saludo disponible');
        }
    }, 2000)
});
```

Ahora, podemos utilizar la promesa `saludar` y utilizar el método `then()`. Lo usamos cuando recibimos un resultado.
Ejecutamos la promesa `saludar`, y cuando tengamos el resultado, ejecutamos el `then()` donde dentro de él tendremos el resultado de la
promesa y ejecutamos el código que tengamos adentro:

```javascript
saludar.then(resultado => {
    alert(resultado);
})
.catch(err => {
    alert(err);
})
```

Lo mostramos dentro de un `alert()`. Y con `catch()` capturamos el posible error.

Si la variable `saludo` fuera `false`:

```javascript
var saludar = new Promise((resolve, reject) => {
    setTimeout(() => {
        let saludo = "Hola muy buenas a todos chavales!!!";
        saludo = false;

        if (saludo) {
            resolve(saludo);
        } else {
            reject('No hay saludo disponible');
        }
    }, 2000)
});
```

Nos devolverá el `reject()`. Con `setTimeout()` le hacemos un `sleep` al código para que se espere un tiempo para ejecutar el bloque de código
dentro de él, de la función de `callback`.

Así se utilizan las promesas, para controlar nuestro código cuando hagamos cosas asíncronas que tarden un rato en completarse. Las librerías
y los frameworks las usan de vez en cuando.