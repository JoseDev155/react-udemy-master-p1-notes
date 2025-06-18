# 21. Instalar React y crear el primer proyecto

Para esto usaremos una aplicación o un paquete de `npm` que se llama `create-react-app`.

## Crear directorio de trabajo

Creamos la carpeta `master-react/`, aquí dentro crearemos los diferentes proyectos que realizaremos en el curso.

## Instalar primer proyecto de React

Abrimos una terminal o símbolo del sistema, nos dirigimos a la carpeta del curso que acabamos de crear:

```bash
cd C:/<ruta-hasta-nuestro-proyecto>/master-react/
```

Limpiamos la consola (opcional):

```bash
cls
```

Y ahora ejecutamos:

```bash
npx create-react-app 01-primeros-pasos
```

* `npx`: Esto ejecuta directamente un paquete, un módulo de Node, de un repositorio de Node.
* `create-react-app`: Módulo que vamos a utilizar con el que podemos crear una aplicación de React.
* `01-primeros-pasos`: Nombre de nuestro primer proyecto de React.

Esto descargará todas las dependencias del proyecto y hará una instalación limpia de React con un proyecto base para empezar a
utilizarlo.

## Documentación de Create React App

Enlace al sitio web de [Create React App](https://create-react-app.dev/).

Simplemente es para hacer un set up de una aplicación web para React.

Ejecutamos este comando:

```bash
npx create-react-app my-app
```

Lo que hace es descargar todas las dependencias, paquetes e instalar lo necesario dentro del proyecto. Instala React, React-DOM, React-Scripts,
diferentes dependencias y todo lo que necesita React para funcionar.

## Comandos de React

Arrancar el proyecto en un pequeño servidor local:

```bash
npm start
```

Generar archivos de producción:

```bash
npm run build
```

Hacer tests:

```bash
npm test
```

Entre otras cosas.

Pero nos sugieren lo más fácil para empezar a desarrollar:

```bash
cd 01-primeros-pasos
npm start
```

Ejecutaremos estos comandos, y esto servirá par ejecutar los scripts que necesitemos y arrancar nuestra aplicación de React en un servidor local.

Y esto se va a quedar escuchando. Cada cambio que hagamos dentro del proyecto, va a estar escuchando esos cambios, va a compilar la aplicación
o refrescar la pantalla cada vez que sea necesario.

Nos dirá que podemos entrar en local o en nuestra red local, ambas en el puerto 3000 para ver nuestro proyecto:

```plaintext
Local:            http://localhost:3000
On Your Network:  http://<ip-address>:3000
```

Entramos a esa dirección en nuestro navegador y veremos la aplicación de React.

Veremos que dice que podemos editar el fichero `src/App.js` y guardar para que se recargue la aplicación.

## Modificando `src/App.js`

Nos vamos a nuestro proyecto, a `src/` que es donde vamos a estar trabajando principalmente, y el fichero que se está visualizando por
pantalla es `App.js`:

```javascript
import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}

export default App;
```

Es un **functional component**, un componente funcional que es una función y la exporta. Y esto ya se ejecuta.

¿Cómo sabemos que aplicación se está ejecutando o qué componente es el primero que se ejecuta? En el `index.js`, veremos que nos indica que es
el `<App />`:

```javascript
import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
import App from './App';
import reportWebVitals from './reportWebVitals';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);

// If you want to start measuring performance in your app, pass a function
// to log results (for example: reportWebVitals(console.log))
// or send to an analytics endpoint. Learn more: https://bit.ly/CRA-vitals
reportWebVitals();
```

Haremos un cambio en `App.js`:

```javascript
function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Bienvenido al master en react!!
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}
```

Guardamos y la pantalla se va a actualizar automáticamente y nos mostrará el párrafo por pantalla.