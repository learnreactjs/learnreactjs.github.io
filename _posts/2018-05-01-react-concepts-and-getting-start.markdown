---
layout: post
title: React - Concepts and Getting Start
date: 2018-05-01
description: React is a UI library developed at Facebook to facilitate the creation of interactive, stateful and reusable UI components.
img: react-concepts-and-getting-start.png
tags: [react, reactjs, learn react]
---

Well, before we start building anything meaningful, its important that we cover some base concepts first, so lets getting start.

## What is React?

React is a UI library developed at Facebook to facilitate the creation of interactive, stateful and reusable UI components. It is used at Facebook in production, and Instagram is written in React.

One of it’s unique points is that not only does it perform on the client side, but it can also be rendered server side, and they can work together inter-operably.

## Concepts

React has quite a small API. This makes it fun to use, easy to learn, and simple to understand. However, being simple does not mean it’s familiar. There are a few concepts to cover before getting started. Let's look at each in turn:

### React Elements

React elements are JavasScript objects which represent HTML elements. They don’t exist in the browser. They represent browser elements such as an h1, div or section.

### JSX

JSX is a technique for creating React elements and components.

### Virtual DOM

The Virtual DOM is a JavaScript tree of React elements and components. React render the Virtual DOM to the browser to make the user interface visible. React observes the Virtual DOM for changes and automatically mutates browser DOM to mach the Virtual DOM.

With a small understanding of these concepts we can move to using React. We will build a series of user interfaces, each adding a layer of functionality on the previous. We will build a photo stream similar to instagram.

### Rendering

The first order of business is rendering a virtual element (a React element or component). Remember, since a virtual element exists only in JavaScript memory, we must explicitly tell React to render it to the browser DOM.

```javascript
ReactDOM.render(
  <h3>Hello World!</h3>,
  document.body
);
```

[Try it on CodePen](https://codepen.io/Bunlong/pen/LmzyWG).

The render function accepts two arguments, a virtual element and a real DOM node. React takes the virtual element and inserts it into the given DOM node.

### Components

Components are the heart and soul of React. They are custom React elements. They are usually extended with unique functionality and structure.

```javascript
class HelloWorld extends React.Component {
  render() {
    return (
      <h1>Hello World!</h1>
    );
  }
}

ReactDOM.render(
  <HelloWorld />, 
  document.body
);
```

[Try it on CodePen](https://codepen.io/Bunlong/pen/MGEmOR).

The createClass function accepts an object which implements a render function.

The Photo component is constructed and rendered to the document body.

This component does nothing more than the previous React image element but it’s ready to be extended with custom functionality and structure.

### Props

Props can be thought of as a component’s options. They are given as arguments to a component and look exactly like HTML attributes.

```javascript
class HelloWorld extends React.Component {
  render() {
    return (
      <h1>{this.props.text}</h1>
    );
  }
}

ReactDOM.render(
  <HelloWorld text="Hello World!" />, 
  document.body
);
```

[Try it on CodePen](https://codepen.io/Bunlong/pen/MGEmqM).

### Specs, Lifecycle & State

The render method is the only required spec for creating a component, but there are serveral lifecycle methods & specs we can use that are mighty helpful when you actually want your component to do anything.

#### Lifecycle Methods:

* `componentWillMount` - Invoked once, on both client & server before rendering occurs.

* `componentDidMount` - Invoked once, only on the client, after rendering occurs.

* `shouldComponentUpdate` - Return value determines whether component should update.

* `componentWillUnmount` - invoked prior to unmounting component.

#### Specs:

* `getInitialState` - Return value is the initial value for state.

* `getDefaultProps` - Sets fallback props values if props are not supplied.

* `mixins` - An array of objects, used to extend the current component’s functionality.

#### State

The state object is internal to a component. It holds data which can change over time.

```javascript
class Trigger extends React.Component {
  state = { liked: false };

  toggleLiked() {
    this.setState({liked: !this.state.liked});
  }

  render() {
    const status = this.state.liked ? 'Liked' : 'Unliked';
    return (
      <div>
        <button onClick={this.toggleLiked.bind(this)}>{status}</button>
      </div>
    );
  }
}

ReactDOM.render(
  <Trigger />, 
  document.body
);
```

[Try it on CodePen](https://codepen.io/Bunlong/pen/ZoXKNE).

Having state in a component introduces a bit more complexity.

The component initial state using `state = { liked: false}`.

The component has another new function toggleLiked. This function calls setState on the component which toggles the liked value.

Within the component`s render function a variable status is assigned either ‘Liked’ or "Unliked" – depending on the liked state.

The button also has an onclick event handler set to the toggleLiked function.

Here’s what happens when the component is rendered to the browser DOM:

* When the component's button is clicked, toggleLiked is called.

* The liked state is changed.

* React re-renders the component to the virtual DOM.

* The new virtual DOM is compared with previous virtual DOM.

* React isolates what has changed and updates the browser DOM.

### Composition

Composition means combining smaller components to form a larger whole. For example the Trigger component could be used inside a TriggerList component.

```javascript
class Trigger extends React.Component {
  state = { liked: false };

  toggleLiked() {
    this.setState({liked: !this.state.liked});
  }

  render() {
    const status = this.state.liked ? 'Liked' : 'Unliked';
    return (
      <div>
        <button onClick={this.toggleLiked.bind(this)}>{status}</button>
      </div>
    );
  }
}

class TriggerList extends React.Component {
  getDataFromServer() {
    return [
      {
        buttonColor: 'red'
      },
      {
        buttonColor: 'blue'
      }
    ];
  }

  render() {
    var data = this.getDataFromServer();

    var lists = data.map(function(photo) {
      return <Trigger />
    });

    return (
      <div>
        {lists}
      </div>
    );
  }
}

ReactDOM.render(<TriggerList />, document.body);
```

[Try it on CodePen](https://codepen.io/Bunlong/pen/aGLwLw).

The Trigger component is exactly the same as before.

There's a new TriggerList component which generates Trigger components. In this case there's some fake server data which return an array of 2 objects, each with a buttonColor.

The data is looped over and will generates 2 Trigger components which are inserted into the return value of the component's render function.

### Events

React also has a built in cross browser events system. The events are attached as properties of components and can trigger methods. Lets make our count increment below using events:

```javascript
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
```

[Try it on CodePen](https://codepen.io/Bunlong/pen/XqegYR).

React events:

* Clipboard Events - `onCopy` `onCut` `onPaste`

* Keyboard Events - `onKeyDown` `onKeyPress` `onKeyUp`

* Focus Events - `onFocus` `onBlur`

* Mouse Events - `onClick` `onDoubleClick` `onDrag` `onDragEnd` `onDragEnter` `onDragExit` `onDragLeave` `onDragOver` `onDragStart` `onDrop` `onMouseDown` `onMouseEnter` `onMouseLeave` `onMouseMove` `onMouseOut` `onMouseOver` `onMouseUp`

* Touch events - `onTouchCancel` `onTouchEnd` `onTouchMove` `onTouchStart`

* UI Events - `onScroll` `onWheel`

* Form Events - `onChange` `onInput` `onSubmit`