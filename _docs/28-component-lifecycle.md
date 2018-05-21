---
title: "Components Lifecycle"
permalink: /component-lifecycle
excerpt: "Components Lifecycle - Learn React"
last_modified_at: 2018-05-19T15:58:49-04:00
---

React components life events are called lifecycle events. These lifecycle events are tied to lifecycle methods.

In the example below, I am console logging the occurrence of the lifecycle events `componentDidMount`, `componentWillUnmount`, and `constructor` lifecycle methods.

<p data-height="265" data-theme-id="dark" data-slug-hash="JvwLvb" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="JvwLvb" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/JvwLvb/">JvwLvb</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

The methods is divided into three (Mounting, Updating, and Unmounting).

## Mounting

> The first of the React Component life cycle is the Mounting. This is where we start initialization of the Component, where Component's props and state are defined.

| Method        | Description   |
|:--------------|:--------------|
| this.state in the constructor |  is invoked before a component is mounted. Stateful components should implement this and return the initial state data. |
| componentWillMount() | is invoked immediately before mounting occurs. |
| componentDidMount() | is invoked immediately after mounting occurs. Initialization that requires DOM nodes should go here. |

## Updating

> The next life cycle is the Growth/Update. We get new props, change state, handle user interactions and communicate with the component hierarchy. This is where we spend most of our time in the Component's lifecycle.

| Method        | Description   |
|:--------------|:--------------|
| UNSAFE_componentWillReceiveProps(object nextProps) | is invoked before a mounted component receives new props. This method should be used to compare this.props and nextProps to perform state transitions using this.setState(). |
| shouldComponentUpdate(object nextProps, object nextState) boolean | is invoked before rendering when new props or state are being received. Implement this as an optimization to compare this.props with nextProps and this.state with nextState and return false if React should skip updating. |
| UNSAFE_componentWillUpdate(object nextProps, object nextState) | is invoked immediately before updating occurs. You cannot call this.setState() here in this method. |
| componentDidUpdate(object prevProps, object prevState, object snapshot) | is invoked immediately after updating occurs. This method is not called for the initial render. |
| getSnapshotBeforeUpdate(object prevProps, object prevState) | is invoked right before the most recently rendered output is committed to the DOM. It enables your component to capture current values before they are potentially changed. |

## Unmounting

> This lifecycle occurs when a component instance is unmounted from the UI. This can occur when the user away, the UI page changes, a component is hidden (like a drawer), etc.

| Method        | Description   |
|:--------------|:--------------|
| componentWillUnmount() | is invoked immediately before a component is unmounted and destroyed. Cleanup should go here. |

Note:

* `componentDidMount` and `componentDidUpdate` are good places to put other libraries logic.
* Mounting
  * Initialize / Construction
  * [prop-types](https://www.npmjs.com/package/prop-types) 
  * `this.state = ...`
  * `componentWillMount()`
  * `render()`
  * `componentDidMount()`
* Updating
  * `UNSAFE_componentWillReceiveProps()`
  * `shouldComponentUpdate`
  * `UNSAFE_componentWillUpdate`
  * `render()`
  * `componentDidUpdate()`
  * `getSnapshotBeforeUpdate()`
* Unmounting
  * `componentWillUnmount()`