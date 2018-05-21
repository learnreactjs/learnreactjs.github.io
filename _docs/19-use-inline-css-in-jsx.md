---
title: "Using Inline CSS in JSX"
permalink: /use-inline-css-in-jsx
excerpt: "Using Inline CSS in JSX - Learn React"
last_modified_at: 2018-05-19T15:58:49-04:00
---

In order to define inline styles on React nodes you need to pass the `style` prop/attribute a JavaScript object or reference to an object containing CSS properties and values.

In the example below I setup a JavaScript object, named `styles`, containing inline styles. Then I use the `{ }` brackets to reference the object that should be used for the value of the style prop/attribute.

<p data-height="265" data-theme-id="dark" data-slug-hash="YLdNwZ" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="YLdNwZ" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/YLdNwZ/">YLdNwZ</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

Notice that, the CSS properties are in a camelCased form similar to what is used when writing [CSS properties in JavaScript](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Properties_Reference). This is required because JavaScript does not allow hyphens in names.+

When the above React/JSX code is transformed by Babel, and then parsed by a JavaScript engine, the resulting HTML will be:

```javascript
<div style="color:red;background-color:black;font-weight:bold;" data-reactid=".0">test</div>
```

Note:

* When specifying a pixel value React will automatically append the string "px" for you after your number value.

