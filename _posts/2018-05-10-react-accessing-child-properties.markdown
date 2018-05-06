---
layout: post
title: React - Accessing Child Properties
date: 2018-05-06
description: When you are building your React components, you'll probably want to access child properties of the markup.
img: react-accessing-child-properties.png
tags: [react, reactjs, learn react]
---

When you are building your React components, you'll probably want to access child properties of the markup.

Parent can read its child by accessing the special `this.props.children`.

For example:

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
            <Button>React <Heart /></Button>
          );
        }
      }

      class Button extends React.Component {
        render() {
          return(
            <button>{this.props.children}</button>
          );
        }
      }

      class Heart extends React.Component {
        render() {
          return (
            <span>Heart</span>
          );
        }
      }

      ReactDOM.render(<App />, document.body);
    </script>
  </body>
</html>
```
[Try it on CodePen](https://codepen.io/Bunlong/pen/PeJBgr).

App has two children Button and Heart, all thoes children come thought from `{this.props.children}`.
