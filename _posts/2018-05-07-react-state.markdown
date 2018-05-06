---
layout: post
title: React - State
date: 2018-05-05
description: 
img: react-state.png
tags: [react, reactjs, learn react]
---

## State

The state object is internal to a component, it holds data which can change over time. So far, we've used React as a static rendering engine. Now, we're going to add state to make React components more dynamic.

The key difference between props and state is that state is internal and controlled by the component itself while props is external and controlled by whatever renders the component. Let's see it in practice:

## State API

### Getinitial State

You can define the initial state by assigning `this.state` in the constructor:

```javascript
constructor(props) {
  super(props);
  this.state = {name: "Brian"};
}
```

### this.state

To access a component's state use `this.state` just like how we use this.props.

### this.setState

To update a component's state, call `this.setState` with an object map of keys to updated values.

Keys that are not provided are not affected.

```javascript
this.setState({
  name: "Ryan"
})
```

When a component's state changes, render is called with the new state and the UI is updated to the new output. This is the heart of React.

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
      class Counter extends React.Component {
        state = { count: 1 };

        incrementCount() {
          this.setState((prevState, props) => ({
            count: prevState.count + 1
          })); 
        }

        render() {
          return (
            <div>
              <h1>Count: {this.state.count}</h1>
                <button type="button" onClick={this.incrementCount.bind(this)}>Increment</button>
            </div>
          );
        }
      }

      ReactDOM.render(<Counter />, document.body);
    </script>
  </body>
</html>
```

[Try it on CodePen](https://codepen.io/Bunlong/pen/XqegYR).
