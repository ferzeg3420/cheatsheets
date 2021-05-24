# Credit to VALENTINO GAGLIARDI for this amazing tutorial:
[valentino's tutorial](https://www.valentinog.com/blog/webpack/) off of which this tutorial is based.

# Glossary

Entry point
: Where the modules to be build are collected by webpack.

Output
: Where webpack puts the builds (transpiled/compiled/preprocessed stuff)

Loaders
: 3rd party extensions: build tools specifically for dealing with various types of files (different file extensions).

Plugins
: 3rd party extensions like loaders but these alter how webpack works.

Modes
: Dev or prod (development or production). Determines if the code is minified, etc.  Dev helps with better error messages (with helpful line numbers and module names) and the ability to see the code with neat variable names and styling.  Prod means faster loads for users.

Code splitting
: Technique for avoiding large bundles. Load stuff when the user does something.  A piece of code that's split is called a //chunk//.


# Startup steps

1. change directory (navigate) into the folder you want to create your project.

1. Run command to start the node package manager: `npm init -y `

1. Run the command to add the webpack module, the command line interface, and a dev
server for testing(optional): ` npm i webpack webpack-cli webpack-dev-server --save-dev `

1. Add an NPM (node package manager) script to (to package.json) run webpack easily:
  in package.json (generated by npm init -y) look for scripts and add the line
  that starts with dev and the one that starts prod:
  `
    "scripts": {
      "dev": "webpack --mode development"
      "prod": "webpack --mode production"
    },
  `

1. When you want to compile/build your project, you can do either: ` npm run dev; npm run prod ` The first is for development mode. The second is for production.

# Config webpack

## Create a webpack.config.js file:
` touch webpack.config.js `

## export modules like in node.js:
```
  module.exports = {
  };
```

## Changing the entry point:
```
  const path = require("path");
  module.exports = {
    entry: { index: path.resolve(__dirname, "source", "index.js") }
  }; 
```

## Changing the output:
```
  const path = require("path");
  module.exports = {
    output: {
      path: path.resolve(__dirname, "build")
    }
  };
```

## config for html:
Requires running: npm i html-webpack-plugin --save-dev

```
const HtmlWebpackPlugin = require("html-webpack-plugin");
const path = require("path");
module.exports = {
  plugins: [
    new HtmlWebpackPlugin({
      template: path.resolve(__dirname, "src", "index.html")
    })
  ]
};
```

# LOADERS

## Syntax:
```
module.exports = {
  module: {
    rules: [
      {
        test: /\.extension$/,
        use: ["loader-b", "loader-a"]
      }
    ]
  },
};
```

## CSS loaders:
In a .js file:
```
  import "./style.css";
```
// Install loaders:
```
  npm i css-loader style-loader --save-dev
```
```
const HtmlWebpackPlugin = require("html-webpack-plugin");
const path = require("path");
module.exports = {
  module: {
    rules: [
      {
        test: /\.css$/,
        use: ["style-loader", "css-loader"]
      }
    ]
  }
};
```
Order of webpack loaders matters!
The loaders are proccessed from right to left and you need css-loader to run
before style-loader because css-loader is for loading the actual css file.

## SASS modules:
in the .js
```
import "./style.scss"; 
```
Requires these modules:
```
npm i css-loader style-loader sass-loader sass --save-dev
```
```
const path = require("path");
module.exports = {
  module: {
    rules: [
      {
        test: /\.scss$/,
        use: ["style-loader", "css-loader", "sass-loader"]
      }
    ]
  }
}; 
```

## Babel modules:
These modules:
```
npm i @babel/core babel-loader @babel/preset-env --save-dev
```
### Configure babel by creating a babel.config.json 
```
{
  "presets": [
    "@babel/preset-env"
  ]
}
```
Configure webpack
```
module.exports = {
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: ["babel-loader"]
      }
    ]
  }
};
```

## React modules:
Download these many modules:
```
npm i @babel/core babel-loader @babel/preset-env @babel/preset-react --save-dev
```
### babel.config.json
```
{
  "presets": ["@babel/preset-env", "@babel/preset-react"]
}
```
// install react with:
// npm i react react-dom
// Configure webpack like with vanilla babel
// could change .js to .jsx
```
module.exports = {
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: ["babel-loader"]
      }
    ]
  }
};
```

## Vue modules:
install these modules:
```
 npm install vue vue-loader vue-template-compiler babel-loader @babel/core @babel/preset-env css-loader vue-style-loader rimraf -D
```
-D adds to the package.json. rimraf reloads when changes are made.
```
module.exports = {
  module: {
    rules: [
      { test: /\.js$/, use: 'babel-loader' },
      { test: /\.vue$/, use: 'vue-loader' },
      { test: /\.css$/, use: ['vue-style-loader', 'css-loader']},
    ]
  },
  plugins: [
    new VueLoaderPlugin(),
  ]
};
```

## Webpack dev server: 
Requires npm i webpack-dev-server --save-dev
which I said was optional

- In package.json:
```
"scripts": {
  "start": "webpack serve --open 'Firefox'",
},
```
- Firefox is the only browser name I know :/ I wonder if the one for chrome is chrome.
- Safari's must be safari. But who knows? Maybe me after I'm done writing this lol.
- Run this script with the shorthand:
```
npm start
```


# I don't know about modules
[ES modules](https://www.valentinog.com/blog/es-modules)


# RIMRAF Cleanup

```
npm install rimraf -D
"scripts": {
  "clean": "rimraf dist",
  "build": "npm run clean && webpack --mode production",
  "serve": "webpack serve --mode development"
},
```