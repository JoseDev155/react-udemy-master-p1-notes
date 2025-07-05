# 47. Creando un proyecto de React

Ahora, vamos a aprender a trabajar con otro hook, el hook `useEffect`.

Se puede conocer como el **hook de el efecto desencadenado** o el hook que produce un efecto cuando algo sucede en la aplicación.

## Creando un nuevo proyecto

Vamos a crear un nuevo proyecto, dentro de nuestro proyecto principal del curso (`master-react/`).

Entramos a la carpeta del proyecto:

```bash
cd C:/ruta-al-proyecto/master-react/
```

Creamos el nuevo proyecto de React `03-use-effect/`:

```bash
npx create-react-app 03-use-effect
```

Una vez terminada la instalación, empezaremos a explicar cómo funciona este hook, para qué sirve y la problemática que puede resolver.

Ahora, arrancamos el proyecto entrando a la carpeta:

```bash
cd 03-use-effect
```

Y ejecutamos:

```bash
npm start
```

## Modificaciones en el proyecto

### Eliminando archivos

* `setupTests.js`
* `reportWebVitals.js`

### Modificando `index.js`

Quitamos las referencias a los archivos eliminados y quitamos el modo estricto de React. Nos debe quedar así:

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

### Creando nuevo directorio

Dentro de `src/`, creamos un nuevo directorio llamado `components/`. Aquí estaremos trabajando con los componentes que vayamos creando.