# 49. Practica con useEffect

Haremos un pequeño ejemplo haciendo un contador con el `useEffect` y, cuando lleguemos a cierta cifra, cambiar por ejemplo la clase de la
etiqueta o cambiar el color de la etiqueta.

## Haciendo un contador

### Creando otro estado

Creando el estado `contador`:

```jsx
const [ contador, setContador ] = useState(0);
```

Nos va a devolver un array con dos propiedades, `contador` y `setContador`. Entonces, vamos a poder actualizar el `contador` cada vez
que se modifique el `usuario`, por ejemplo.

Vamos a hacer que cada vez que se modifique el `usuario` se lance este efecto, pero además, este efecto también va a hacer uso del
`setContador`. Lo que vamos a hacer es actualizar `contador` sumándole `1` a lo que ya tuviera:

```jsx
useEffect(() => {
    console.log("Has modificado el usuario !!");

    setContador(contador+1);
}, [usuario]);
```

También queremos que indique este `console.log()`, por eso lo vamos a poner abajo, aparte de que diga que has modificado el `usuario` queremos
que nos indique el número de veces que lo han modificado:

```jsx
useEffect(() => {
    setContador(contador+1);
    console.log("Has modificado el usuario: "+contador);
}, [usuario]);
```

Si actualizamos la pantalla, nos dice `0`. Si modificamos el nombre, se va sumando y nos dice el número de veces que hemos hecho una modificación
en el `usuario` o que se ha detectado una modificación en el `usuario` y por lo tanto estamos lanzando un efecto desencadenado.

Si queremos que el `useEffect` en la etiqueta del `usuario` cuando se produce X número de cambios en el `contador`, podemos hacer una condición
ternaria aquí y que imprima `label` en una situación y que imprima `label-green` en otra. Es decir, abrimos llaves `{}` aquí:

```jsx
<strong className={ contador >= 10 ? 'label label-green' : 'label' }>{usuario}</strong>
```

Imprimimos `label label-green` si `contador >= 10`, y si no que simplemente imprima `label`.

Veremos que cuando detecta los `10` cambios lo pone en verde.

Pero esto, nos sirve igual si en lugar del `usuario` queremos detectar y lanzar el efecto solamente cuando cambiamos la `fecha`:

```jsx
useEffect(() => {
    setContador(contador+1);
    console.log("Has modificado el usuario: "+contador);
}, [fecha]);
```

Si cambiamos `10` veces la `fecha`, el `useEffect` lo detecta y va sumando en el `contador` y cambia la etiqueta a verde.

Y como ahora estamos trabajando con la `fecha`, podríamos cambiar esta condición a la etiqueta de la `fecha`:

```jsx
<strong>{usuario}</strong>
<strong className={ contador >= 10 ? 'label label-green' : 'label' }>{fecha}</strong>
```

Nos la pone normal, y cuando cambiamos la `fecha` `10` veces, nos pone la etiqueta verde. Y esto lo estamos haciendo todo con el `useEffect`.

Pero también podríamos hacerlo para que se aplicara a los dos:

```jsx
useEffect(() => {
    setContador(contador+1);
    console.log("Has modificado el usuario: "+contador);
}, [fecha, usuario]);
```

Cuando se detecten `10` cambios, da igual si es de la `fecha` o del `usuario`, cuando se ejecute `10` veces este `useEffect`, entonces vamos
a cambiar el color de la etiqueta.

Y esto funciona. Porque el `useEffect` se está lanzando cuando hacemos cambios en estas propiedades y solamente se ejecuta una vez cuando
cargamos el componente, porque tenemos también el otro `useEffect`.

**NOTA**: Lo recomendable es siempre tener `useEffect`'s separados para los diferentes estados que queremos estar comprobando que cambian para
detectar los diferentes estados. No hacerlo todos juntos.

Está es una parte de la **reactividad** en React, y de la instantaneidad, y de las cosas que podríamos llegar a hacer.

El `useEffect` es muy importante, lo veremos sobre todo cuando desarrollemos alguna aplicación y queramos que se detecte el cambio de
algún estado o queramos que cuando pase X cosa en la aplicación, se lance un efecto o se actualice un listado de elementos o un listado de
cosas que vienen por **Ajax** o lo que sea, justo cuando se carga la aplicación al principio o cuando se hace alguna modificación en algún componente.