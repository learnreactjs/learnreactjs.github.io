---
title: "Rendering to DOM"
permalink: /render-to-dom
excerpt: "Rendering to DOM - Learn React"
last_modified_at: 2018-05-16T15:58:49-04:00
---

React provides the `ReactDOM.render()` function from `react-dom js` that can be used to render React nodes to the DOM. We've already seen this `render()` function in use in this chapter.

In the example below, using `ReactDOM.render()`, the `<option>` and `<foo-bar>` React nodes are rendered to the DOM.

<p data-height="265" data-theme-id="dark" data-slug-hash="xjJBeQ" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="xjJBeQ" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/xjJBeQ/">xjJBeQ</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

Once rendered to the DOM, the HTML will be:

```
<body>
  <div id="app1"><option value="1" data-reactid=".0">one</option></div>
  <div id="app2"><foo-bar classname="bar" children="foo" data-reactid=".1">foo</foo-bar></div>
</body>
```

The `ReactDOM.render()` function is initially how you get the React nodes to the Virtual DOM, then to the HTML DOM.