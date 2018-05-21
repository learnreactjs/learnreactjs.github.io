---
title: "Using Refs and DOM"
permalink: /use-refs-and-dom
excerpt: "Using Refs and DOM - Learn React"
last_modified_at: 2018-05-19T15:58:49-04:00
---

In React data-flow, props are the only way that parent components interact with their children. To modify a child, you re-render it with new props. However, there are a few cases where you need to modify a child outside of the data-flow. The child to be modified could be an instance of a React component, or it could be a DOM node/element.

> Refs provide a way to access DOM nodes or React elements created in the render method.

## Creating Refs

Refs are created using `React.createRef()` and attached to React elements via the ref attribute.

Refs are assigned to an instance property when a component is constructed, so they can be referenced throughout the component.

```javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.myRef = React.createRef();
  }

  render() {
    return <div ref={this.myRef} />;
  }
}
```

## Accessing Refs

When a ref is passed to an element in `render`, a reference to the node becomes accessible at the current attribute of the `ref`.

```javascript
const node = this.myRef.current;
```

The value of the `ref` depending on the type of the node. You may not use the `ref` attribute on functional components because they don’t have instances.

## Adding a Ref to a DOM Element

In the example below I use a `ref` to store a reference to a DOM node:

<p data-height="265" data-theme-id="dark" data-slug-hash="ZowOEV" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="ZowOEV" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/ZowOEV/">ZowOEV</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

React will assign the `current` property with the DOM element when the component mounts, and assign it back to `null` when it unmounts. `ref` updates happen before `componentDidMount` or `componentDidUpdate` lifecycle hooks.

## Adding a Ref to a Class Component

If you want to wrap the `TextInput` above to being clicked immediately after mounting, we could use a ref to get access to the custom input and call its `focusTextInput` method manually:

<p data-height="265" data-theme-id="dark" data-slug-hash="LmqZZp" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="LmqZZp" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/LmqZZp/">LmqZZp</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

Note: This only works if `TextInput` is declared as a class.

## Refs and Functional Components

**Note:** You may not use the `ref` attribute on functional components because they don't have instances:
{: .notice--warning}

```javascript
function MyFunctionalComponent() {
  return <input />;
}

class Parent extends React.Component {
  constructor(props) {
    super(props);
    this.textInput = React.createRef();
  }
  render() {
    // This will *not* work!
    return (
      <MyFunctionalComponent ref={this.textInput} />
    );
  }
}
```

You should convert the component to a class if you need a `ref` to it, just like you do when you need lifecycle methods or state.

You can, however, use the ref attribute inside a functional component as long as you refer to a DOM element or a class component:

<p data-height="265" data-theme-id="dark" data-slug-hash="zjeKOB" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="zjeKOB" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/zjeKOB/">zjeKOB</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

## Callback Refs

React also supports another way to set `refs` called "callback refs", which gives more fine-grain control over when refs are set and unset.

Instead of passing a `ref` attribute created by `createRef()`, you pass a function. The function receives the React component instance or HTML DOM element as its argument, which can be stored and accessed elsewhere.

In the example below I implements a common pattern: using the `ref` callback to store a reference to a DOM node in an instance property:

<p data-height="265" data-theme-id="dark" data-slug-hash="qYgaEj" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="qYgaEj" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/qYgaEj/">qYgaEj</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

React will call the `ref callback` with the DOM element when the component mounts, and call it with `null` when it unmounts. `ref callbacks` are invoked before `componentDidMount` or `componentDidUpdate` lifecycle hooks.

You can pass callback refs between components like you can with object refs that were created with `React.createRef()`.

<p data-height="265" data-theme-id="dark" data-slug-hash="zjeKvK" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="zjeKvK" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/zjeKvK/">zjeKvK</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

`Parent` passes its `ref` callback as an `inputRef` prop to the `TextInput`, and the `TextInput` passes the same function as a special ref attribute to the `<input>`. As a result, `this.inputElement` in `Parent` will be set to the DOM node corresponding to the `<input>` element in the `TextInput`.

Note:

* When to Use Refs
  * Managing focus, text selection, or media playback.
  * Triggering imperative animations.
  * Integrating with third-party DOM libraries.
* Avoid using refs for anything that can be done declaratively.
