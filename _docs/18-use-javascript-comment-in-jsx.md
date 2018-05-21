---
title: "Using JavaScript Comments in JSX"
permalink: /use-javascript-comment-in-jsx
excerpt: "Using JavaScript Comments in JSX - Learn React"
last_modified_at: 2018-05-18T15:58:49-04:00
---

You can place JavaScript comments anywhere in React/JSX you want except locations where JSX might expect a React child node. In this situation you'll have to escape the comment using { } so that JSX knows to pass that on as actual JavaScript.

Make sure you understand where you'll have to tell JSX to pass along a JS comment so a child React node is not created.

```javascript
var reactNode = <div /*comment*/>{/* use {'{}'} here to comment*/}</div>;
```

In the above code if I had not wrapped the comment inside of the `<div>` with `{ }` brackets then Babel would have converted the comment to a React text node. The outcome, unintentionally, without the `{ }` would be:

```javascript
var reactNode = React.createElement(
  "div",
  null,
  "/* use ",
  "{}",
  " here to comment*/"
);
```

Which would result in the following HTML that would have unintended text nodes.

```javascript
<div data-reactid=".0">
  <span data-reactid=".0.0">/* use </span>
  <span data-reactid=".0.1">{}</span>
  <span data-reactid=".0.2"> here to comment*/</span>
</div>
```