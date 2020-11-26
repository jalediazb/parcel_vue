# Pediente

- Error Scoped Sytiles
- Eliminar los ficheros anteriormente generados en la carpeta ./docs



# Proceso de Creación

## Git y NPM

1. Crear Repositorio Git
   1. `git init`
   2. `git remote add origin url`
2. Crear `.gitignore`
3. Iniciar NPM: `npm init -y`
   1. `npm install --save vue`
   2. `npm install --save-dev parcel-bundler`
4. Crear fichero .gitignore

``````http://localhost:1234
node_modules/
dist/
.cache/
npm-debug.log
yarn-error.log
``````

## Crear estructura de ficheros:

```public
public
	index.html
src
	assets
	components
	main.js
	App.vue
```
index.html:
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <div id="app"></div>
    <script src="../src/main.js"></script>
</body>
</html>
```

main.js:

```js
import Vue from 'vue'
import App from './App'

new Vue({
  el: '#app',
  render: h => h(App)
})
```

App.vue:

```js
<template>
  <div class="container">
    <h1>{{ message }}</h1>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      message: 'Proyecto Vue y Parcel',
    };
  },
};
</script>

<style>
  
</style>
```



## Añadir Scripts a package.json

```js
"scripts": {
    "dev": "parcel ./public/index.html --out-dir docs",
    "build": "parcel build ./public/index.html --out-dir docs --public-url ./"
  }
```

Se utiliza como carpeta de salida `docs` para poder publicar fácilmente en Github Pages



## Eslint

`npm install eslint eslint-plugin-vue babel-eslint --save-dev`

```js
// Fichero .eslintrc.js

module.exports = {
  root: true,
  env: {
    node: true,
  },
  extends: ["plugin:vue/essential", "eslint:recommended"],
  parserOptions: {
    parser: "babel-eslint",
  },
  rules: {},
};
```



## Bulma

`npm install bulma`

add to main.js

```js
import '../node_modules/bulma/css/bulma.css';
```



## purgecss

`npm install -D parcel-plugin-purgecss`

```javascript
//purgecss.config.js

module.exports = {
  content: ["./public/index.html", "./src/**/*.vue", "./src/*.vue"],
  defaultExtractor(content) {
    const contentWithoutStyleBlocks = content.replace(
      /<style[^]+?<\/style>/gi,
      ""
    );
    return (
      contentWithoutStyleBlocks.match(/[A-Za-z0-9-_/:]*[A-Za-z0-9-_/]+/g) || []
    );
  },
  safelist: [
    /-(leave|enter|appear)(|-(to|from|active))$/,
    /^(?!(|.*?:)cursor-move).+-move$/,
    /^router-link(|-exact)-active$/,
    /data-v-.*/,
  ],
};
```


