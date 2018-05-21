---
title: "Rendering JSX to DOM"
permalink: /render-jsx-to-dom
excerpt: "Rendering JSX to DOM - Learn React"
last_modified_at: 2018-05-18T15:58:49-04:00
---

The `ReactDOM.render()` function can be used to render JSX to the DOM. Actually, after Babel transforms the JSX all it is doing is rendering nodes created by `React.createElement()`.

In the example I am rendering a `<option>` element to the DOM using JSX.

<p data-height="265" data-theme-id="dark" data-slug-hash="odJLPe" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="odJLPe" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/odJLPe/">odJLPe</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

Once rendered to the DOM, the HTML will look like so:

```javascript
<body>
  <div id="app"><option value="1" data-reactid=".0">one</li></div>
</body>
```

Babel is taking the JSX in your JavaScript files transforming it to React nodes (React.createElement()) then using these nodes created by React (the Virtual DOM) as a template for creating a real html DOM branch. The part where the React nodes are turned into the real DOM nodes and added to the DOM in an HTML page occurs when ReactDOM.render() is called.
