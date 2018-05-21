---
title: "Mentioning to a Component Instance"
permalink: /mention-to-a-component-instance
excerpt: "Mentioning to a Component Instance - Learn React"
last_modified_at: 2018-05-19T15:58:49-04:00
---

When a component is `render()`, a React component instance is created. One can gain access to this instance and it's properties (e.g., this.props) and methods (e.g. this.setState()) in two ways.

The first way is by using the `this` keyword from within lifecycle methods. In the example below all of the `console.log(this)` statements will mention to the component instance.

<p data-height="265" data-theme-id="dark" data-slug-hash="rvooeW" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="rvooeW" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/rvooeW/">rvooeW</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

The other way to gain a reference to a component instance involves making use of the return value from calling `ReactDOM.render()`. In other words, the `ReactDOM.render()` function will return a reference to the top most rendered component.

<p data-height="265" data-theme-id="dark" data-slug-hash="mLaarz" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="mLaarz" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/mLaarz/">mLaarz</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

Note:

* The `this` keyword will commonly be used from within a component to access instance properties like `this.props.[NAME OF PROP]`, `this.props.children`, and `this.state`. It will also be used to call class methods/properties, that all components share like `this.setState`.