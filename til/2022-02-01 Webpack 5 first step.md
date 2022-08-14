- By default (no webpack.config.js file), webpack build command will look for src/index.js file for bundling.
- Basic config:
_webpack.config.js_

```js
const path = require('path')
module.exports = {
  entry: './src/index.js' // entry points at the entry point of the application
  // or it can be object like below for code splitting (break code into smaller chunks):
  // entry: {
  //    foo: 'foo.js',
  //    bar: 'bar.js'
  // }
  // output is the objects contain:
  //  1. name of the file we want to set for compiled file, by default it's main.js
  //  2. path
  output: {
    filename: 'awesome.js',
    path: path.resolve(__dirname, 'dist'),
  }
  // loader
  
}
```

- If we need to compile stylesheet file with preprocessor like scss, make it noticed to webpack by importing it to the entry point js file.

_src/index.js_
```js
import './style.scss';
console.log('Hello world')
```

Notes: we need a **loader** to process the file because it is not javascript code.
use `npm install ...(loader packages)` to install loaders. In this case:

```
npm i -D css-loader style-loader sass-loader
```

_webpack.config.js_

```js
module.exports = {
  ...
  // we can add one or more rules regarding to the types of file we want webpack to compile
  module: {
    rules: [
      {
        // test attribute: regexp that matches the type of file we want the loader to run on
        test: /\.scss$/,
        // loaders to process file
        use: [
          'style-loader',
          'css-loader',
          'sass-loader',
        ]
      },
    ]
  }
}
```
- Hot reload: webpack-dev-server
```
npm i -D webpack-dev-server
```

_src/index.js_
```js
module.exports = {
  ...
  devServer: {
    contentBase: path.join(__dirname, 'public'),
    port: 3000
  }
}
```

_package.json_
```json
  ...
  "scripts": {
    "build": "webpack",
    "dev": "webpack serve",
  }
```