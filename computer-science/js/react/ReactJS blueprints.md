# ReactJS blueprints

## Three principles of React

React is declarative and not imperative
Component Based design
Learn once, write anywhere

## Inherited properties of React

displayName, propTypes are for debugging
getInitialState, getDefaultProps are for initial data
componentDidMount & componentShouldUpdate are lifecycle events

React.createClass defines a variable

`React.createClass ({`
`	render(){`
`		return (`
`			JSX goes here`
`		)`
`	}`
`})`

You can call getDefaultProps and set default values if u anticipate that the prop will be used at a later point in the component’s lifecycle.

`getDefaultProps() {`
`  return {`
`    greeting: ""`
`  }`
`}`

Similarly, setInitialState can be called to set default State

`setInitialState() {`
`  return {`
`    greeting: "Hello world!"`
`  }`
`}`

To set the revised value, manipulate the initial state object using setState

ELEMENT START : span
`getInitialState: function () {`ELEMENT END : span

ELEMENT START : span
`  return {`ELEMENT END : span

ELEMENT START : span
`    random_number: 0`ELEMENT END : span

ELEMENT START : span
`  }`ELEMENT END : span

ELEMENT START : span
`},`ELEMENT END : span

ELEMENT START : span
`componentDidMount(){`ELEMENT END : span

ELEMENT START : span
`  setInterval(()=>{`ELEMENT END : span

ELEMENT START : span
`    this.setState({`ELEMENT END : span

ELEMENT START : span
`      random_number: Math.random()*100`ELEMENT END : span

ELEMENT START : span
`    });`ELEMENT END : span

ELEMENT START : span
`  },1000)`ELEMENT END : span

ELEMENT START : span
`},`ELEMENT END : span

ELEMENT START : span
`render() {`ELEMENT END : span

ELEMENT START : span
`  return (`ELEMENT END : span

ELEMENT START : span
`    <div>{this.state.random_number}</div>`ELEMENT END : span

ELEMENT START : span
`  );`ELEMENT END : span

ELEMENT START : span
`}`ELEMENT END : span

setState triggers component re-render.

Statics are methods that can be called on the component.

ELEMENT START : span
`import React from 'react';`ELEMENT END : span

ELEMENT START : span
`const App = React.createClass ({`ELEMENT END : span

ELEMENT START : span
`  statics: {`ELEMENT END : span

ELEMENT START : span
`    myMethod: (foo) => {`ELEMENT END : span

ELEMENT START : span
`      return foo == "bar";`ELEMENT END : span

ELEMENT START : span
`    }`ELEMENT END : span

ELEMENT START : span
`  },`ELEMENT END : span

ELEMENT START : span
`  render() {`ELEMENT END : span

ELEMENT START : span
`    return null;`ELEMENT END : span

ELEMENT START : span
`  }`ELEMENT END : span

ELEMENT START : span
`});`ELEMENT END : span

ELEMENT START : span
`console.log(App.myMethod('bar'));  // true`ELEMENT END : span

PropTypes allow you to validate props being passed to your components. This is an optional tool to help when developing apps and will show up in the console log if props don’t match the spec.

ELEMENT START : span
`propTypes: {`ELEMENT END : span

ELEMENT START : span
`  myOptionalObject: React.PropTypes.object,`ELEMENT END : span

ELEMENT START : span
`  aRequiredString: React.PropTypes.string.isRequired,`ELEMENT END : span

ELEMENT START : span
`  anOptionalNumber: React.PropTypes.number,`ELEMENT END : span

ELEMENT START : span
`  aValueOfAnyKind: React.PropTypes.any,`ELEMENT END : span

ELEMENT START : span
`  customProp: function(props, propName, componentName) {`ELEMENT END : span

ELEMENT START : span
`    if (!/matchme/.test(props[propName])) {`ELEMENT END : span

ELEMENT START : span
`      return new Error('Validation failed!');`ELEMENT END : span

ELEMENT START : span
`    }`ELEMENT END : span

ELEMENT START : span
`  }`ELEMENT END : span

ELEMENT START : span
`}`ELEMENT END : span

You can set a display Name to the component using the displayName key

`displayName: "My component Name"`

Initially all lifecycle methods are set to empty except shouldComponentUpdate (which defaults to true)

## Sequence of lifecycle method trigger

1. **componentDidMount** : do not run setState here. It will lead to an endless loop. Call it in componentWillMount instead

`componentDidMount() {`
`  // Executed after the component is mounted`
`}`

1. **componentWillMount** : this method is executed both on server and client side apps

`componentWillMount() {`
`  // Executed before the component is mounted `
`}`

1. **shouldComponentUpdate** : default value is true. If you override it and return tase, the component  will never be updated despite prop and state updates. This can be used to conditionally update components. Speed improvements if you set it false.

1. **componentWillReceiveProps** : componentWillReceiveProps(abject nextProps) in order to access incoming props using nextProps. setState will not trigger a re-render. Use componentWillUpdate if you want a re-render

`componentWillReceiveProps(nextProps) {`
`  // you can compare nextProps with this.props`
`  // and optionally set a new state or execute functions`
`  // based on the new props`
`}`

1. componentWillUpdate : componentWillUpdate(object nextProps, object nextState) in order to access incoming props and state. Calling setState will lead to an endless loop. setState needs to be called in componentWillReceiveProps

`componentWillUpdate (nextProps) {`
`  // you can compare nextProps with this.props `
`  // or nextState with this.state`
`}`

1. componentDidUpdate : executed whenever the component receives new props or states and the render method has already been executed.

`componentDidUpdate() {`
`  // Execute functions after the component has been updated`
`}`

1. componentWillUnmount : It is invoked before a component is unmounted from the DOM. If you need to clean up memory or invalidate timers this is the place to do it.

`componentWillUnmount() {`
`  // Execute functions before the component is unmounted`
`  // from the DOM`
`}`

## DOM & Virtual DOM

React needs closing tags. JSX follows strict match between opening and closing tags. 

Need to attach refs if you want to getElementById
React.findDOMNode(this.refs.myReference)

Events that are passed are a synthetic instance of the actual event with the same props as the native event. It is cross browser compatible.

If you want to capture event immediately, onClick can be rewritten as onClickCapture and so on.

event.stopPropagation() or event.preventDefault() work just fine.
Ref: https://facebook.github.io/react/docs/events.html

ELEMENT START : span
`import React from 'react';`ELEMENT END : span

ELEMENT START : span
`import {render} from 'react-dom';`ELEMENT END : span

ELEMENT START : span

ELEMENT END : span

ELEMENT START : span
`const App = React.createClass ({`ELEMENT END : span

ELEMENT START : span

ELEMENT END : span

ELEMENT START : span
`  getInitialState() {`ELEMENT END : span

ELEMENT START : span
`    return {`ELEMENT END : span

ELEMENT START : span
`      greeting: "",`ELEMENT END : span

ELEMENT START : span
`      message: ""`ELEMENT END : span

ELEMENT START : span
`    }`ELEMENT END : span

ELEMENT START : span
`  },`ELEMENT END : span

ELEMENT START : span

ELEMENT END : span

ELEMENT START : span
`  componentWillMount() {`ELEMENT END : span

ELEMENT START : span
`    this.setState ({`ELEMENT END : span

ELEMENT START : span
`      greeting: this.props.greeting`ELEMENT END : span

ELEMENT START : span
`    });`ELEMENT END : span

ELEMENT START : span
`  },`ELEMENT END : span

ELEMENT START : span

ELEMENT END : span

ELEMENT START : span
`  componentDidMount() {`ELEMENT END : span

ELEMENT START : span
`    this.refs.input.focus();`ELEMENT END : span

ELEMENT START : span
`  },`ELEMENT END : span

ELEMENT START : span

ELEMENT END : span

ELEMENT START : span
`  handleClear: function (event) {`ELEMENT END : span

ELEMENT START : span
`    this.refs.input.value="";`ELEMENT END : span

ELEMENT START : span
`    this.setState ({`ELEMENT END : span

ELEMENT START : span
`      message: ""`ELEMENT END : span

ELEMENT START : span
`    });`ELEMENT END : span

ELEMENT START : span
`  },`ELEMENT END : span

ELEMENT START : span

ELEMENT END : span

ELEMENT START : span
`  handleChange: function (event) {`ELEMENT END : span

ELEMENT START : span
`    this.setState ({`ELEMENT END : span

ELEMENT START : span
`      message: event.target.value`ELEMENT END : span

ELEMENT START : span
`    });`ELEMENT END : span

ELEMENT START : span
`  },`ELEMENT END : span

ELEMENT START : span

ELEMENT END : span

ELEMENT START : span
`  render: function () {`ELEMENT END : span

ELEMENT START : span
`    return (`ELEMENT END : span

ELEMENT START : span
`      <div>`ELEMENT END : span

ELEMENT START : span
`        <h1>Refs and data binding</h1>`ELEMENT END : span

ELEMENT START : span
`        <h2>{this.state.greeting}</h2>`ELEMENT END : span

ELEMENT START : span
`        Type a message:`ELEMENT END : span

ELEMENT START : span
`        <br/>`ELEMENT END : span

ELEMENT START : span
`        <input type="text" ref="input"`ELEMENT END : span

ELEMENT START : span
`          onChange={this.handleChange} />`ELEMENT END : span

ELEMENT START : span
`        <br/>`ELEMENT END : span

ELEMENT START : span
`        Your message: {this.state.message}`ELEMENT END : span

ELEMENT START : span
`        <br/>`ELEMENT END : span

ELEMENT START : span
`        <input type="button"`ELEMENT END : span

ELEMENT START : span
`          value="Clear"`ELEMENT END : span

ELEMENT START : span
`          onClick={this.handleClear}`ELEMENT END : span

ELEMENT START : span
`        />`ELEMENT END : span

ELEMENT START : span
`      </div>`ELEMENT END : span

ELEMENT START : span

ELEMENT END : span

ELEMENT START : span
`    );`ELEMENT END : span

ELEMENT START : span
`  }`ELEMENT END : span

ELEMENT START : span

ELEMENT END : span

ELEMENT START : span
`});`ELEMENT END : span

ELEMENT START : span

ELEMENT END : span

ELEMENT START : span
`render (`ELEMENT END : span

ELEMENT START : span
`  <App greeting="Let's bind some values" />,`ELEMENT END : span

ELEMENT START : span
`    document.getElementById('#app')`ELEMENT END : span

ELEMENT START : span
`);`ELEMENT END : span

## Composition

**After **

ELEMENT START : span
`npm init`ELEMENT END : span

**Do **

ELEMENT START : span
`npm install –-save babelify@7.2.0 browserify-middleware@7.0.0 express@4.13.3 react@0.14.3 reactify@1.1.1 browser-sync@2.10.0 babel-preset-react@6.3.13 babel-preset-es2015@6.3.13 browserify@12.0.1 react-dom@0.14.3 watchify@3.6.1`ELEMENT END : span

**Babel config**

ELEMENT START : span
`{`ELEMENT END : span

ELEMENT START : span
`  "presets": ["es2015","react"]`ELEMENT END : span

ELEMENT START : span
`}`ELEMENT END : span

**server.js file**

ELEMENT START : span
`var express = require("express");`ELEMENT END : span

ELEMENT START : span
`var browserify  = require('browserify-middleware');`ELEMENT END : span

ELEMENT START : span
`var babelify = require("babelify");`ELEMENT END : span

ELEMENT START : span
`var browserSync = require('browser-sync');`ELEMENT END : span

ELEMENT START : span
`var app = express();`ELEMENT END : span

ELEMENT START : span
`var port = process.env.PORT || 8080;`ELEMENT END : span

ELEMENT START : span

ELEMENT END : span

ELEMENT START : span
`browserify.settings ({`ELEMENT END : span

ELEMENT START : span
`  transform: [babelify.configure({`ELEMENT END : span

ELEMENT START : span
`  })],`ELEMENT END : span

ELEMENT START : span
`  presets: ["es2015", "react"],`ELEMENT END : span

ELEMENT START : span
`  extensions: ['.js', '.jsx'],`ELEMENT END : span

ELEMENT START : span
`  grep: /\.jsx?$/`ELEMENT END : span

ELEMENT START : span
`});`ELEMENT END : span

ELEMENT START : span
 ELEMENT END : span

ELEMENT START : span
`// serve client code via browserify`ELEMENT END : span

ELEMENT START : span
`app.get('/bundle.js', browserify(__dirname+'/source/app.jsx'));`ELEMENT END : span

ELEMENT START : span

ELEMENT END : span

ELEMENT START : span
`// resources`ELEMENT END : span

ELEMENT START : span
`app.get(['*.png','*.jpg','*.css','*.map'], function (req, res) {`ELEMENT END : span

ELEMENT START : span
`  res.sendFile(__dirname+"/public/"+req.path);`ELEMENT END : span

ELEMENT START : span
`});`ELEMENT END : span

ELEMENT START : span

ELEMENT END : span

ELEMENT START : span
`// all other requests will be routed to index.html`ELEMENT END : span

ELEMENT START : span
`app.get('*', function (req, res) {`ELEMENT END : span

ELEMENT START : span
`  res.sendFile(__dirname+"/public/index.html");`ELEMENT END : span

ELEMENT START : span
`});`ELEMENT END : span

ELEMENT START : span

ELEMENT END : span

ELEMENT START : span
`// json`ELEMENT END : span

ELEMENT START : span
`app.get('*.json', function (req, res) {`ELEMENT END : span

ELEMENT START : span
`  res.sendFile(__dirname+"/public/"+req.path);`ELEMENT END : span

ELEMENT START : span
`});`ELEMENT END : span

ELEMENT START : span

ELEMENT END : span

ELEMENT START : span
`// Run the server`ELEMENT END : span

ELEMENT START : span
`app.listen(port,function() {`ELEMENT END : span

ELEMENT START : span
`  browserSync ({`ELEMENT END : span

ELEMENT START : span
`    proxy: 'localhost:' + port,`ELEMENT END : span

ELEMENT START : span
`        files: ['source/**/*.{jsx}','public/**/*.{css}'],`ELEMENT END : span

ELEMENT START : span
`    options: {`ELEMENT END : span

ELEMENT START : span
`      ignored: 'node_modules'`ELEMENT END : span

ELEMENT START : span
`    }`ELEMENT END : span

ELEMENT START : span
`  });`ELEMENT END : span

ELEMENT START : span
`});`ELEMENT END : span

**index.html looks like**

ELEMENT START : span
`<!DOCTYPE html>`ELEMENT END : span

ELEMENT START : span
`<html>`ELEMENT END : span

ELEMENT START : span
`  <head>`ELEMENT END : span

ELEMENT START : span
`    <title>ReactJS Blueprints</title>`ELEMENT END : span

ELEMENT START : span
`    <meta charset="utf-8">`ELEMENT END : span

ELEMENT START : span
`    <link rel="stylesheet" href="app.css" />`ELEMENT END : span

ELEMENT START : span

ELEMENT END : span

ELEMENT START : span
`  </head>`ELEMENT END : span

ELEMENT START : span
`  <body>`ELEMENT END : span

ELEMENT START : span
`    <div id="container"></div>`ELEMENT END : span

ELEMENT START : span
`      <script src="bundle.js"></script>`ELEMENT END : span

ELEMENT START : span
`  </body>`ELEMENT END : span

ELEMENT START : span

ELEMENT END : span

ELEMENT START : span
`</html>`ELEMENT END : span

**Router.jsx depends on react router that needs to be imported to app.jsx**

ELEMENT START : span
`"use strict";`ELEMENT END : span

ELEMENT START : span

ELEMENT END : span

ELEMENT START : span
`import React from "react";`ELEMENT END : span

ELEMENT START : span
`import Layout from './layout.jsx';`ELEMENT END : span

ELEMENT START : span
`import { Router, Route, browserHistory } from 'react-router'`ELEMENT END : span

ELEMENT START : span

ELEMENT END : span

ELEMENT START : span
`const Routes = (`ELEMENT END : span

ELEMENT START : span
`  <Router history={browserHistory}>`ELEMENT END : span

ELEMENT START : span
`      <Route handler={Layout} path="/">`ELEMENT END : span

ELEMENT START : span
`      </Route>`ELEMENT END : span

ELEMENT START : span
`  </Router>`ELEMENT END : span

ELEMENT START : span
`);`ELEMENT END : span

ELEMENT START : span

ELEMENT END : span

ELEMENT START : span
`module.exports = Routes;`ELEMENT END : span

**A file that returns a blank component looks like**

ELEMENT START : span
`"use strict";`ELEMENT END : span

ELEMENT START : span

ELEMENT END : span

ELEMENT START : span
`import React from "react";`ELEMENT END : span

ELEMENT START : span

ELEMENT END : span

ELEMENT START : span
`const Layout = React.createClass ({`ELEMENT END : span

ELEMENT START : span
`  render() {`ELEMENT END : span

ELEMENT START : span
`    return (`ELEMENT END : span

ELEMENT START : span
`      <div>`ELEMENT END : span

ELEMENT START : span
`        { React.cloneElement(`ELEMENT END : span

ELEMENT START : span
`          this.props.children,`ELEMENT END : span

ELEMENT START : span
`          this.state`ELEMENT END : span

ELEMENT START : span
`        ) }`ELEMENT END : span

ELEMENT START : span
`      </div>`ELEMENT END : span

ELEMENT START : span
`    );`ELEMENT END : span

ELEMENT START : span
`  }`ELEMENT END : span

ELEMENT START : span
`});`ELEMENT END : span

ELEMENT START : span

ELEMENT END : span

