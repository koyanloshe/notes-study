# Boilerplate Node project

`npm install webpack webpack-cli webpack-dev-server --save-dev`
` `
`npm install @babel/cli @babel/core @babel/node @babel/preset-env @babel/preset-react @babel/register --save-dev`
` `
`npm install babel-loader style-loader css-loader`
` `
` `
` `
`{`
`"presets": [`
`"@babel/preset-env",`
`"@babel/preset-react"`
`]`
`}`
` `
` `
`// Imports: Dependencies`
`const path = require('path');`
**`const htmlWebpackPlugin = require('html-webpack-plugin')`**

`require("babel-register");`
`// Webpack Configuration`
`const config = {`
` `
`// Entry`
`entry: {'PATH TO YOUR INDEX.JSX FILE'},`
`  // Output`
`output: {`
`path: path.resolve(__dirname, 'PATH TO SEND BUNDLED/TRANSPILED CODE'),`
`filename: 'bundle.js',`
`},`
`  // Loaders`
`module: {`
`rules : [`
`// JavaScript/JSX Files`
`{`
`test: /\.jsx$/,`
`exclude: /node_modules/,`
`use: ['babel-loader'],`
`},`
`// CSS Files`
`{`
`test: /\.css$/,`
`use: ['style-loader', 'css-loader'],`
`}`
`]`
`},`
***`// Plugins`***

**`plugins: [`**

**`new htmlWebpackPlugin({`**

**`template: './client/dist/index.html',`**

**`filename: 'index.html',`**

**`hash: true`**

**`})`**

**`],`**

**`// OPTIONAL`**

**`// Reload On File Change`**

**`watch: true,`**

**`// Development Tools (Map Errors To Source File)`**

**`devtool 'source-map',`**

`};`
`// Exports`
`module.exports = config;`
` `
` `
_`https://medium.com/@jeffrey.allen.lewis/the-ultimate-2018-webpack-4-and-babel-setup-guide-npm-yarn-dependencies-compared-entry-points-866b577da6a`_

` `
`babel-preset-es2015`

