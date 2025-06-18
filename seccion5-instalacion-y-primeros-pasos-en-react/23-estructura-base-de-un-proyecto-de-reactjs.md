# 23. Estructura base de un proyecto de React.js

## Directorio `node_modules/`

Es el directorio donde se van a descargar y se van a guardar todos los paquetes y dependencias del proyecto. No hay que tocarlo.

## Archivo `package.json`

Cuando lo modifiquemos y agreguemos una dependencia o un paquete nuevo para instalar, cuando ejecutemos:

```bash
npm update
```

O el:

```bash
npm install
```

Se van instalar todas esas dependencias y se van a guardar los archivos dentro de `node_modules/`.

Aquí indicamos la versión del proyecto, las dependencias, scripts, y diferentes cosas para configurar nuestro proyecto. Sobre todo
dependencias y scripts que van a ser usados frecuentemente en la terminal.

## Directorio `public/`

Es el directorio público donde se va a cargar la web, o básicamente, el HTML que va a cargar la web principalmente. Que tendrá acceso directo en
el navegador.

La página de inicio de nuestro proyecto, no podría verse si no pasara antes por un `index.html` dentro del directorio `public/`.

* El `favicon.ico` es el icono que se carga en la pestaña del navegador.

* El `index.html` es la página principal y dentro de ella se va a estar cargando toda la aplicación dentro de `<div id="root">`. Aun también se pueden cargar dependencias, estilos CSS, SEO, cambiar atributo HTML, etc.

* Tenemos los logos `logo192.png` y `logo512.png`. Imágenes que luego se podrían utilizar para los iconos de las aplicaciones PWA.

* El `manifest.json` también es un fichero para configurar una aplicación PWA.

Una **PWA** (Progressive Web App) es una Aplicación Web Progresiva, que la usamos en nuestro navegador pero nos permite instalarla en un
dispositivo móvil. Una especie de instalación que nos permite abrir esa aplicación como si fuese nativa, pero realmente no lo es y esta cargando
la web.

* El `robots.txt` es para la parte de SEO, para decirle a las arañas de Google y los buscadores que URL's del proyecto pueden ser leídas, cuáles
no, que indexar, que no, que está permitido acceder y que no.

## Directorio `src/`

Es el principal en el que vamos a estar trabajando, los otros no tanto.

* El `App.css` es un fichero de estilos del componente `App.js`.

* El componente `App.js` es el componente principal que haya hora mismo.

* El `App.test.js` es un fichero de test para el componente `App.js`.

* El `index.css` que vendría a ser la hoja de estilos principal del proyecto principal o del punto de entrada de la aplicación que sería el `index.js`.

* En el `index.js` se carga el framework de React, y se carga también o se indica cuál es el componente por el cual va a empezar la aplicación, que en este caso es el `App.js` o el componente `<App />`. También indicamos en que etiqueta del `index.html` que vimos antes se va a cargar todo el componente y toda la aplicación como tal de React, en este caso en el `<div id="root">`. Esto es lo que viene por defecto.

* Luego tenemos el `logo.svg`, que es una imagen, es la imagen que vemos en la página de inicio del proyecto.

* El `reportWebVitals.js` que es para el tema de PWA.

* El `setupTests.js` sirve para el tema de configuración de tests.

## Archivo `.gitignore`

Fuera del directorio `src/` tenemos el `.gitignore`, que es para incluir cosas que no queremos que se incluyan en los `commit`'s que hagamos.
Aquí, incluimos los archivos y directorios que no queremos que se suban a un repositorio remoto y se van a ignorar.

## Archivo `package-lock.json`

Es un fichero que genera el `package.json` o `npm` cuando trabajamos con ellos.

## Archivo `README.md`

Es documentación de lo que es React, de cómo funciona un poco, son cuatro puntos básicos de Create React App sobre todo.