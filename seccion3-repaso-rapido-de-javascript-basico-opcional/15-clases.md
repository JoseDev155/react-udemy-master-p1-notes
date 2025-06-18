# 15. Clases

Creamos un nuevo fichero `clases.js` donde trabajaremos con las clases. Y cargamos el fuchero en el `index.html`:

```html
<script src="clases.js" type="text/javascript"></script>
```

## Definición de clases

Las **clases** en Programación Orientada a Objetos, son un molde que nos van a permitir generar objetos de un tipo concreto similares unos de
otros.

## Ejemplo de clases

### Crear clases

Las clases se crean usando la palabra reservada `class`. Con el `constructor()` creamos diferentes propiedades dentro de nuestra clase:

```javascript
class Coche {
    constructor() {
        this.modelo = '';
        this.velocidad = '';
        this.antiguedad = '';
    }

    aumentarVelocidad() {
        this.velocidad += 1;
    }

    reducirVelocidad() {
        this.velocidad -= 1;
    }
}
```

Con TypeScript, se hace un poco diferente.

El `constructor()` es el método principal, que se va a ejecutar siempre que una clase se carga.

Una clase va a tener **propiedades**, que son las características generales que tiene esa clase en concreto.
Luego, hay **métodos**, que son las funciones o acciones que es capaz de hacer ese objeto cuando lo creemos. Es prácticamente como una función.

Con `this` accedemos a las propiedades del objeto.

Podemos tener métodos que asignen valores a las propiedades. También podemos asignar valores en el `constructor()` cada vez que creemos el
objeto:

```javascript
constructor(modelo, velocidad, antiguedad) {
    this.modelo = modelo;
    this.velocidad = velocidad;
    this.antiguedad = antiguedad;
}
```

Así le damos valores por defecto.

### Crear objetos

Creamos una variable:

```javascript
var coche1 = new Coche('BMW', 200, 2017);
```

Y así podemos ir creando diferentes coches, un coche es un coche, tienen las mismas características y funciones, y métodos o acciones. Pero los datos del coche son diferentes, las características varian:

```javascript
var coche1 = new Coche('BMW', 200, 2017);
var coche2 = new Coche('Audi', 100, 2018);
var coche3 = new Coche('Mercedes', 200, 2017);
var coche4 = new Coche('Renault', 200, 2017);
```

El valor de las propiedades cambian. Utilizamos el molde de la clase `Coche` para ir generando diferentes objetos.

Mostraremos los datos:

```javascript
console.log(coche1);
console.log(coche2);
```

Veremos el objeto de JavaScript en la consola del navegador.

Si ejecutamos un método entre medias y volvemos a imprimir por consola `coche1`:

```javascript
console.log(coche1);
coche1.aumentarVelocidad();
coche1.aumentarVelocidad();
coche1.aumentarVelocidad();

console.log(coche1);
```

La velocidad se habrá modificado en ambas impresiones por consola. La `velocidad` en ambas ahora será `203`.

Si mostramos la `velocidad` en el documento HTML:

```javascript
document.write("<h1>Velocidad: " + coche1.velocidad + "</h1>");
coche1.aumentarVelocidad();
coche1.aumentarVelocidad();
coche1.aumentarVelocidad();
```

Nos muestra `200`. Si luego de ejecutar los métodos de ``, imprimimos los mismo:

```javascript
document.write("<h1>Velocidad: " + coche1.velocidad + "</h1>");
coche1.aumentarVelocidad();
coche1.aumentarVelocidad();
coche1.aumentarVelocidad();
document.write("<h1>Velocidad: " + coche1.velocidad + "</h1>");
```

Ahora será `203`. Estos métodos modifican el objeto para que tenga valores diferentes y modifican las propiedades de ese objeto.