---
title: "Using JavaScript Expressions in JSX"
permalink: /use-javascript-expression-in-jsx
excerpt: "Using JavaScript Expressions in JSX - Learn React"
last_modified_at: 2018-05-18T15:58:49-04:00
---

What happens when you want to intermingle real JavaScript code within JSX? To write a JavaScript expression within JSX you will have to surround the JavaScript code in `{ }` brackets.

In the React/JSX code below I am mixing JavaScript expressions (e.g. `2+2`), surround by `{ }` among the JSX that will eventually get evaluated by JavaScript.

<p data-height="265" data-theme-id="dark" data-slug-hash="xjmRgB" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="xjmRgB" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/xjmRgB/">xjmRgB</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

The JSX transformation will result in the follow:

```javascript
var label = '2 + 7';
var inputType = 'input';

var reactNode = React.createElement(
  'label',
  null,
  label,
  ' = ',
  React.createElement('input', { type: inputType, value: 2 + 7 })
);

ReactDOM.render(reactNode, document.getElementById('app'));
```

Once this code is parsed by a JavaScript engine (i.e. a browser) the JavaScript expressions are evaluated and the resulting HTML will look like so:

```javascript
<div id="app">
  <label data-reactid=".0"><span data-reactid=".0.0">2 + 7</span><span data-reactid=".0.1"> = </span><input type="input" value="9" data-reactid=".0.2"></label>
</div>
```

Nothing that complicated is going on here once you realize that the brackets basically escape the JSX. The `{ }` brackets simply tells JSX that the content is JavaScript so leave it alone so it can eventually be parsed by a JavaScript engine (e.g. 2+7). Note that `{ }` brackets can be used anywhere among the JSX expressions as long as the result is valid JavaScript.

Note:

* If you have to escape brackets (i.e. you want brackets in a string) use `{'{}'}`.
