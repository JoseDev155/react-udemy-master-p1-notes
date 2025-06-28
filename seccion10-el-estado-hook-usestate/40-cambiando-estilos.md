# 40. Cambiando estilos

Vamos a cambiar un poco los estilos que tiene por defecto la aplicación en `App.css`. Quitamos el `margin-top` de la clase `.App-logo`:

```css
.App-logo {
  height: 20vmin;
  pointer-events: none;
}
```

Y modificamos el `justify-content` que es la alineación vertical que tiene todo el contenido dentro de la clase `.App-header`, cambiamos de `center` a `flex-start`:

```css
.App-header {
  background-color: #282c34;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  font-size: calc(10px + 2vmin);
  color: white;
}
```

Para que arranque al principio de la página. Así queda mucho mejor, y si inspeccionamos el elemento, no se va a ocultar el logo ni nada,
simplemente va a cambiar un poco el tamaño.