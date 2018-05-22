---
title: "Creating Stateless Function Components"
permalink: /create-stateless-function-component
excerpt: "Creating Stateless Function Components - Learn React"
last_modified_at: 2018-05-21T15:58:49-04:00
---

When a component is purely a result of `props` alone, no `state`, the component can be written as a pure function avoiding the need to create a React component instance. 

In the example below `MyComponent` is the result of a function that returns the results from `React.createElement()`.

<p data-height="265" data-theme-id="dark" data-slug-hash="ELrJWN" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="ELrJWN" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/ELrJWN/">ELrJWN</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

Having look at the same code not using JSX should clarify what is going on.

```javascript
var MyComponent = function MyComponent(props) {
  return React.createElement(
    "div",
    null,
    "Hello ",
    props.name
  );
};

ReactDOM.render(React.createElement(MyComponent, { name: "doug" }), app);
```

Constructing a React component without create React class is typically referred to as a stateless function component.

Stateless function components can't be passed component options (i.e. `render`, `componentWillUnmount`, etc.). However `prop-types` can be used.

The example below demonstrates a stateless function component making use of `prop-types`.

<p data-height="265" data-theme-id="dark" data-slug-hash="OZdGEG" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="OZdGEG" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/OZdGEG/">OZdGEG</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

Note:

* Make as many of your components as possible, as stateless components.