---
title: "Creating React Nodes"
permalink: /create-react-node
excerpt: "Creating React Nodes - Learn React"
last_modified_at: 2018-05-16T15:58:49-04:00
---

Most developers using React will prefer JSX and use it to create React nodes. Otherwise, in this chapter we are going to test how React nodes can be created without JSX, using only JavaScript. The next chapter we will discuss creating React nodes using JSX.

Creating React nodes using JavaScript is as simple as calling the `React.createElement(type, props, children)` function and passing it a set of arguments defining an actual DOM node (e.g. type = an html element e.g. `<option>` or custom element e.g. `<my-option>`).

The `React.createElement()` arguments:

  * `type (string | createReactClass())`: can be a string which represents an HTML element (or custom HTML element) or React component instance (i.e., an instance of createReactClass()).
  * `props (null | object)`: can be `null` or an object containing attributes/props and values.
  * `children (null | string | createReactClass() | React.createElement())`: children can be null, a string that gets turned into a text node, an instance of createReactClass() or React.createElement()

Below I use the `React.createElement()` function to create a virtual DOM representation of a `<option>` element node containing a text node of one (React text) and with value 1.

```
var reactNodeOption = React.createElement('option', { value: 1 }, "one");
```

Notice that the first argument defines the HTML element I want to represent. The second argument defines the attributes/props on the `<option>`. And the third argument defines what the node inside of the element will be. In this case, I am placing a child text node (i.e. 'one') inside the `<option>`. The last argument that becomes a child of the node being created can be:

* A React text node
* A React element node, or
* A React component instance

So far I've done is creating a React element node containing a React text node that I have stored into the variable reactNodeOption. To create a virtual DOM we have to actually render the React element node to a real DOM. To do this we use the `ReactDOM.render()` function:

```
ReactDOM.render(reactNodeOption, document.getElementById('app'));
```

The above code, invokes the following:

* Create a virtual DOM constructed from the React element node passed in (reactNodeOption)
* Use the virtual DOM to re-construct a real DOM branch
* Insert the real DOM branch (i.e. `<option value="1">one</option>`) into the DOM as a child node of `<div id="app"></div>`.

The HTML DOM changes from this:

```
<div id="app"></div>
```

To

```
<div id="app">
  // Note that React automatically added the react data-reactid attribute
  <option value="1" data-reactid=".0">one</option>
</div>
```

This was a simplistic example.

Let use `React.createElement()` to create a complex structure. For example, below I'm using `React.createElement()` to create a bunch of React nodes representing an HTML select (i.e. `<select>`).

```
// Create React element <option>
var rElmOption1 = React.createElement('option', { value: 1 }, "one"),
    rElmOption2 = React.createElement('option', { value: 2 }, "two"),
    rElmOption3 = React.createElement('option', { value: 3 }, "three"),
    rElmOption4 = React.createElement('option', { value: 4 }, "four");

// Create <select> React element and add child
// React <option> elements to it
var reactElementUl = React.createElement('select', {className: 'mySelect'}, rElmOption1, rElmOption2, rElmOption3, rElmOption4);
```

When the above code is rendered to the DOM the result HTML will look like:

```
<select class="mySelect" data-reactid=".0">
  <option value="1" data-reactid=".0.0">one</li>
  <option value="2" data-reactid=".0.1">two</li>
  <option value="3" data-reactid=".0.2">three</li>
  <option value="4" data-reactid=".0.3">four</li>
</ul>
```

You can try this yourself using the CodePen below:

<p data-height="265" data-theme-id="dark" data-slug-hash="XqBGaz" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="XqBGaz" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/XqBGaz/">XqBGaz</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

We can realize that React nodes are just JavaScript objects in a tree that represent real DOM nodes inside of a virtual DOM tree. The virtual DOM is then used to construct an actual DOM branch in an HTML page.

