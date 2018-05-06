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
<script crossorigin src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
```

But I would like to recommend using [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/lang/en/) for managing front-end dependencies.

To install React with Yarn, run:

```javascript
yarn init
yarn add react react-dom babel-cli babel-preset-react
```

To install React with npm, run:

```javascript
npm init
npm install --save react react-dom babel-cli babel-preset-react
```

## Getting start with Hello World

Let create a `helloworld.html` file with the following contents:

```javascript
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Learn React</title>
    <script crossorigin src="https://unpkg.com/react@16/umd/react.production.min.js"></script>
    <script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.production.min.js"></script>
    <script crossorigin src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
  </head>
  <body>
    <script type="text/jsx">
      class App extends React.Component {
        render() {
          return (
            <h1>Hello World!</h1>
          );
        }
      }

      ReactDOM.render(
        <App />, 
        document.body
      );
    </script>
  </body>
</html>
```

[Try it on CodePen](https://codepen.io/Bunlong/pen/KRXQvG).

The above code we create a `h1 element` in `App component` and render it in body DOM.
