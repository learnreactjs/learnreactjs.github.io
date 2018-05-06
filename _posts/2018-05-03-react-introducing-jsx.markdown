---
layout: post
title: React - Introducing JSX
date: 2018-05-03
description: JSX is a JavaScript syntax extension that looks similar to XML. You can use a simple JSX transform with React.
img: react-introducing-jsx.png
tags: [react, reactjs, learn react]
---

## What is JSX?

JSX is a ***JavaScript syntax extension*** that looks similar to XML. You can use a simple JSX transform with React.

It’s more familiar for casual developers such as designers.

XML has the benefit of balanced opening and closing tags. This helps make large trees easier to read than function calls or object literals.

## Why JSX?

You don’t have to use JSX with React. You can just use plain JS. However, I recommend using JSX because it is a concise and familiar syntax for defining tree structures with attributes.

## Get started

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

Look at the code above we create an `App` class which render `h1` with text `Hellow World`; that looks very similar to XML syntax or HTML tag.

## Transform

React JSX transforms from an XML-like syntax into native JavaScript. XML elements, attributes and children are transformed into arguments that are passed to React.createElement.

```javascript
// Input (JSX):
<App />;

// Output (JS):
React.createElement(App);
```
