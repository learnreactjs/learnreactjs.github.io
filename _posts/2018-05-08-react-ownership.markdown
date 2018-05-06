---
layout: post
title: React - Ownership
date: 2018-05-06
description: In React, an owner is the component that sets the props of other components. 
img: react-ownership.png
tags: [react, reactjs, learn react]
---

In React, an owner is the component that sets the props of other components. 

More formally, if a component X is created in component Y's render() method, it is said that X is owned by Y.

Exercises:

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
        constructor(props) {
          super(props);
          this.state = {txt: ''}
        }

        update(e) {
          this.setState({txt: e.target.value});
        }

        render() {
          return (
            <div>
              <Widget txt={this.state.txt} update={this.update.bind(this)} />
              <Widget txt={this.state.txt} update={this.update.bind(this)} />
            </div>
          );
        }
      }

      class Widget extends React.Component {
        render() {
          return (
            <div>
              <input type="text" onChange={this.props.update} />
              <br />
              <b>{this.props.txt}</b>
            </div>
          );
        }
      }

      ReactDOM.render(<App txt="this is the txt prop" />, document.body);
    </script>
  </body>
</html>
```

[Try it on CodePen](https://codepen.io/Bunlong/pen/ZoXjzE).

The exercises above Widget component is owned by App component.
