---
layout: post
title: React - Getting Start with Hello World
date: 2018-05-02
description: 
img: react-getting-start-with-hello-world.png
tags: [react, reactjs, learn react]
---

React is built around the concept of components. This is in contrast to frameworks like Angular and Ember, which use two-way data bindings to update the HTML of the page. 

In my opinion React is easier to learn than Angular and Ember – it is much smaller and plays nicely with jQuery and other frameworks. It is also extremely fast, because it uses a virtual DOM, and syncs only the changed parts with the underlying page.

## How to use?

The React library can be used directly from the Facebook CDN to increase the performance of the page load by including the link below in header tag:

```html
<script crossorigin src="https://unpkg.com/react@16/umd/react.production.min.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.production.min.js"></script>
```

But I would like to recommend using [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/lang/en/) for managing front-end dependencies.

To install React with Yarn, run:

```javascript
yarn init
yarn add react react-dom
```

To install React with npm, run:

```javascript
npm init
npm install --save react react-dom
```

## Getting start with Hello World

Let create a `helloworld.html` file with the following contents:

```javascript
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Hello World</title>
    <script crossorigin src="https://unpkg.com/react@16/umd/react.production.min.js"></script>
    <script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.production.min.js"></script>
  </head>
  <body>
    <script type="text/javascript">
      var App = React.createClass({
        render: function() {
          return React.createElement("h1", null, "Hello World")
        }
      });

      React.render(React.createElement(App), document.body);
    </script>
  </body>
</html>
```

The primary type in React is the ReactElement. It has four properties: type, props, key and ref. It has no methods and nothing on the prototype. We can create a element through `React.createElement`.

To render a new tree into the DOM, we create `ReactElements` and pass them to `React.render` along with a regular DOM Element.

In codes above we create a `h1 element` in `App component` and render it in body DOM.

## Getting start with Hello World - Separate File

Let create a `helloworld.js` file with the following contents:

```javascript
<!-- helloworld.js -->
var App = React.createClass({
  render: function() {
    return React.createElement("h1", null, "Hello World")
  }
});

React.render(React.createElement(App), document.body);

```

Update HTML file as below:

```javascript
<!-- helloworld.html -->
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Hello World</title>
    <script src="react.js"></script>
  </head>
  <body>
    <script src="helloworld.js"></script>
  </body>
</html>
```