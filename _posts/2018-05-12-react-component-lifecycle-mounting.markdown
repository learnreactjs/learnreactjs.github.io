---
layout: post
title: React - Component Lifecycle Mounting
date: 2018-05-08
description: 
img: react-component-lifecycle-mounting.png
tags: [react, reactjs, learn react]
---

React mounting have 3 methods:

* `this.state` in the constructor: object is invoked before a component is mounted. Stateful components should implement this and return the initial state data.

* `componentWillMount()`: is invoked immediately before mounting occurs.

* `componentDidMount()`: is invoked immediately after mounting occurs. Initialization that requires DOM nodes should go here.

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
      class Button extends React.Component {
        constructor(props) {
          super(props);
          this.state = {val: 0};
        }
        
        handleUpdate() {
          this.setState((prevState, props) => ({
            val: prevState.val + 1
          })); 
        }

        componentWillMount() {
          console.log('mounting');
        }

        render() {
          console.log('rendering');
          return (
            <div>
              <button onClick={this.handleUpdate.bind(this)}>{this.state.val}</button>
            </div>
          );
        }

        componentDidMount() {
          console.log('mounted');
        }
      }

      class App extends React.Component {
        handleMount() {
          ReactDOM.render(<Button />, document.getElementById('app'));
        }

        render() {
          return(
            <div>
              <button onClick={this.handleMount}>Mount</button>
              <button onClick={this.handleUnmount}>Unmount</button>
              <div id="app"></div>
            </div>
          );
        }
      }

      ReactDOM.render(<App />, document.body);
    </script>
  </body>
</html>
```

[Try it on CodePen](https://codepen.io/Bunlong/pen/ELoEmj).

In Button component `this.state = {val: 0}` initial val: 0 by default.

When you click on Mount button, `componentWillMount()` method is invoked immediately before mounting occurs, and `render()` method render button into body DOM, and then `componentDidMount()` method is invoked immediately after mounting occurs.