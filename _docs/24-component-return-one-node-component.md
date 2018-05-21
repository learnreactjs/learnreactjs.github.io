---
title: "Components Return One Node/Component"
permalink: /component-return-one-node-component
excerpt: "Components Return One Node/Component - Learn React"
last_modified_at: 2018-05-19T15:58:49-04:00
---

The `render()` method defined when creating a component should return only one React node (or, component). This one node/component can contain any number of children. In the code below the `<reactNode>` is the starting node. Inside of this node any number of sibling and child nodes can be returned.

<p data-height="265" data-theme-id="dark" data-slug-hash="rvoQGN" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="rvoQGN" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/rvoQGN/">rvoQGN</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

Note that if you want to return React nodes on more than one line (taking advantage of whitespace) you will have to surround the returned value in `()`. In the code below the JSX defining (i.e. rendered) the `MyComponent` is returned in `()`.

<p data-height="265" data-theme-id="dark" data-slug-hash="LmMXQx" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="LmMXQx" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/LmMXQx/">LmMXQx</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

An error will occur if more than one React node is returned. If you think about it, the error occurs because returning two `React.createElement()` functions isn't possible with JavaScript as below:

<p data-height="265" data-theme-id="dark" data-slug-hash="MGZzGN" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="MGZzGN" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/MGZzGN/">MGZzGN</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

The above code will result in the following error:

```
Uncaught SyntaxError: embedded: Adjacent JSX elements must be wrapped in an enclosing 

return (
  <span>test</span>
  <span>test</span>
);
```

Commonly, developers will add a wrapping element `<div>` element to avoid this error.

This issue also concerns components. Just like React nodes, if you are returning a component, only one component can be returned but that component can have unlimited children.

<p data-height="265" data-theme-id="dark" data-slug-hash="bMOQxQ" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="bMOQxQ" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/bMOQxQ/">bMOQxQ</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>
