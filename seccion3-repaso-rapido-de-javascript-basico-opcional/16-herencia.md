# 16. Herencia

## Definición de herencia

Es cuando tenemos una **clase padre**, como puede ser `Coche`, y luego creamos otra clase que va a heredar todas las propiedades y métodos de la
clase padre.

## Ejemplo de herencia

### `extends` y `super()`

Creamos otra clase y **extendemos** la clase `Coche`, esta clase va a tener los mismos valores que tiene `Coche`.

Al `constructor` le podemos pasar los mismos datos que le estamos pasando a `Coche`, porque los valores son los mismos.

Usamos `super()` y le pasamos los valores del `constructor()`, y así le pasamos los valores a las propiedades de la clase padre:

```javascript
class Autobus extends Coche {
    constructor(modelo, velocidad, antiguedad) {
        super(modelo, velocidad, antiguedad);
    }
}
```

Ahora, crearemos un objeto de `Autobus` y lo imprimiremos por consola:

```javascript
var autobus1 = new Autobus('PEGASUS', 200, 2017);
console.log(autobus1);
```

Veremos los datos correctamente, y además, son las mismas propiedades que tiene la clase padre que es `Coche`.

### Agregar más propiedades y métodos

Podemos tomar como base la clase `Coche`, heredamos de ella para tener las mismas propiedades y métodos, pero podemos utilizar nuevas
propiedades y crear otro método:

```javascript
class Autobus extends Coche {
    constructor(modelo, velocidad, antiguedad) {
        super(modelo, velocidad, antiguedad);
        this.altura = 5;
    }

    mostrarAltura() {
        return "La altura del bus es: " + this.altura;
    }
}
```

Y entonces, podemos utilizar ese método:

```javascript
var autobus1 = new Autobus('PEGASUS', 200, 2017);
console.log(autobus1.mostrarAltura());
```

Veremos el mensaje en la consola del navegador.

Para eso sirve la herencia, para traernos las cualidades de una clase padre a una clase hija, la cual va a ser similar pero va a tener algunas
pequeñas diferencias en cuanto a propiedades y métodos que tiene la clase.