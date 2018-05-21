---
title: "Creating React components"
permalink: /create-react-component
excerpt: "Creating React components - Learn React"
last_modified_at: 2018-05-19T15:58:49-04:00
---

## Functional Components

You can define a component using JavaScript function:

```javascript
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

This function is a React component because it accepts a single "props" object argument and returns a React element. We call such components "functional components" because they are literally JavaScript functions.

## Class Components

You can also use an [ES6](https://babeljs.io) class to define a component.

The most important component lifecycle method is `render()`. This method is required and is a method that returns React nodes and components. All other lifecycle methods are optional.

The following example of creating a Timer React component from React nodes using ES6 class to define a component:

<p data-height="265" data-theme-id="dark" data-slug-hash="JvwLvb" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="JvwLvb" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/JvwLvb/">JvwLvb</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

It looks like a lot of code. However, the bulk of the code simply involves creating a `<Timer/>` component using ES6 class with 4 lifecycle methods (constructor, componentDidMount, componentWillUnmount, render).

Notice that `Timer` is capitalized. When creating custom React components you need to capitalize the name of the component. Additionally, We'll discuss the component API in more detail at the end of this chapter.

Once a component is mounted (i.e. created) you can use the component API. The api contains two methods:

| API method        | Example   | Description    |    
|:------------------|:--------------|:--------------| 
| [setState()](https://reactjs.org/docs/react-component.html#setstate)    | this.setState({mykey: 'my new value'}); <br/><br/> this.setState(function(previousState, currentProps) { return {myInteger: previousState.myInteger + 1}; }); | Primary method used to re-render a component and sub components. |
| [forceUpdate()](https://reactjs.org/docs/react-component.html#forceupdate) | this.forceUpdate(function() { //callback });  | Calling forceUpdate() will cause render() to be called on the component, skipping shouldComponentUpdate(). |

The available component lifecycle methods are listed below:

| Functions     | Description   |
|:--------------|:--------------|
| [render()](https://reactjs.org/docs/react-component.html#render)      | A required value, typically a function that returns React nodes, other React components, or null/false. |
| [constructor()](https://reactjs.org/docs/react-component.html#constructor) | Callback function is called before it is mounted, the right place to initialize state, is used to bind event handlers to the class instance. |
| [displayName](https://reactjs.org/docs/react-component.html#displayname)      | String, naming the component, used in debugging messages. If using JSX this is set automatically. |
| [UNSAFE_componentWillMount()](https://reactjs.org/docs/react-component.html#unsafe_componentwillmount) | Callback function invoked before mounting occurs, called before `render()`. |
| [componentDidMount()](https://reactjs.org/docs/react-component.html#componentdidmount) | Callback function invoked immediately after a component is mounted. |
| [UNSAFE_componentWillReceiveProps()](https://reactjs.org/docs/react-component.html#unsafe_componentwillreceiveprops) | Callback function invoked before a mounted component receives new props. |
| [shouldComponentUpdate()](https://reactjs.org/docs/react-component.html#shouldcomponentupdate) | Callback function invoked before rendering when new props or state are being received. |
| [UNSAFE_componentWillUpdate()](https://reactjs.org/docs/react-component.html#unsafe_componentwillupdate) | Callback function invoked immediately before rendering when new props or state are being received. |
| [componentDidUpdate()](https://reactjs.org/docs/react-component.html#componentdidupdate) | Callback function invoked immediately after updating occurs. |
| [componentWillUnmount()](https://reactjs.org/docs/react-component.html#componentwillunmount) | Callback function invoked immediately before a component is unmounted and destroyed. |
| [getDerivedStateFromProps()](https://reactjs.org/docs/react-component.html#static-getderivedstatefromprops) | Callback function invoked after a component is instantiated as well as when it receives new props. |
| [getSnapshotBeforeUpdate()](https://reactjs.org/docs/react-component.html#getsnapshotbeforeupdate) | Callback function invoked right before the most recently rendered output is committed,  it enables your component to capture current values (e.g. scroll position) before they are potentially changed. |
