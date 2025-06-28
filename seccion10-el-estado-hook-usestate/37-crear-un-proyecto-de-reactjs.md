# 37. Crear un proyecto de ReactJS

Ya hemos visto los primeros pasos en React y ahora vamos a ver algún que otro **Hook**.
Vamos a empezar con el estado de React y con el **Hook** `useState`.

Si tenemos activo el proyecto `01-primeros-pasos/`, ejecutamos `Ctrl+C` en la consola de comandos.

Hacemos:

```bash
cls
```

Y luego:

```bash
cd ..
```

Esto para ir al directorio raíz de nuestro curso.

## Creando un nuevo proyecto de React

Esto lo haremos para tener una referencia en nuestros apuntes, y con cada mini sección del curso, con cada cosa relevante para separarlo,
vamos creando diferentes carpetas para diferenciarlos, diferentes carpetas de un proyecto de React.

Ejecutaremos:

```bash
npx create-react-app 02-use-state
```

Con esto creamos la segunda carpeta del curso `02-use-state/`. De momento, esa va a ser la nomenclatrua de carpetas en cuanto a secciones
del curso o apuntes que vayamos haciendo en el curso.

Le damos a **Enter** y esto va  acrear nuestro nuevo proyecto, descargando todas las dependencias.

Aquí es donde vamos a estar trabajando a partir de ahora.

Antes de arrancar el proyecto, vamos a eliminar algunas cosas. Como por ejemplo:

* `setupTests.js`
* `reportWebVitals.js`

Y eliminamos las referencias a estos archivos en el `index.js`, y también quitamos el modo estricto para que no nos moleste. El `index.js`
debería quedar tal que así:

```jsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
import App from './App';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <App />
);
```

Ahora, ya podemos arrancar nuestro proyecto haciendo:

```bash
cd 02-use-state
```

Y arrancar el servidor local de React:

```bash
npm start
```

Y veremos en el navegador nuestro proyecto base de React.