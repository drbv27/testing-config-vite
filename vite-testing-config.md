# Instalación y configuracion de Jest + React Testing Library
## En proyectos de React + Vite

1. Instalaciones:
```
npm install jest babel-jest @babel/preset-env @babel/preset-react --save-dev
npm install @testing-library/react @types/jest jest-environment-jsdom --save-dev
```

2. Opcional: Si usamos Fetch API en el proyecto:
```
npm install whatwg-fetch --save-dev
```

3. Actualizar los scripts del __package.json__
```
"scripts: {
  ...
  "test": "jest --watchAll"
```

4. Crear la configuración de babel __babel.config.js__
```
module.exports = {
    presets: [
        [ '@babel/preset-env', { targets: { esmodules: true, node: "current" } } ],
        [ '@babel/preset-react', { runtime: 'automatic' } ],
    ],
};
```

5. Opcional, pero eventualmente necesario, crear Jest config y setup:

__jest.config.js__
```
export default = {
    testEnvironment: 'jest-environment-jsdom',
    setupFiles: ['./jest.setup.js']
}
```

__jest.setup.js__
```
// En caso de necesitar la implementación del FetchAPI
import 'whatwg-fetch'; // <-- yarn add whatwg-fetch
```

6. eliminar de __package.json__
```
"type":"module",
```
// En caso de necesitar la implementación del FetchAPI
import 'whatwg-fetch'; // <-- yarn add whatwg-fetch
```
7. si usas react 18
```
- elimina  el jest.config.js
- en lugar d ecrear el babel.config.js crea: babel.config.json:
    {
  "presets": [
    [
      "@babel/preset-env",
      {
        "targets": {
          "node": "current"
        }
      }
    ]
  ]
}
- crea el archivo .babelrc:
    {
  "presets": ["@babel/preset-env", "@babel/preset-react"]
}
```
// En caso de necesitar la implementación del FetchAPI
import 'whatwg-fetch'; // <-- yarn add whatwg-fetch
```


