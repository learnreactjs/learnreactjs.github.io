---
title: "Re-rendering A Component"
permalink: /re-render-a-component
excerpt: "Re-rendering A Component - Learn React"
last_modified_at: 2018-05-19T15:58:49-04:00
---

You would realize that calling `ReactDom.render()` is the initial of the rendering of a component and all sub components.

After the initial mounting of components, a re-rendering will occur when:

* A component's `setState()` method is called.
* A component's `forceUpdate()` method is called.

In the example below `ReactDOM.render(< App / >, app);` starts the first cascade of rendering, rendering `<App />` and `<Timer/>`. The next re-render occurs when the `setInterval()` calls the `setState()` component method, which causes `<App />` and `<Timer/>` to be re-rendered. Note the UI changes when the `now state` is changed.

<p data-height="265" data-theme-id="dark" data-slug-hash="odmzaM" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="odmzaM" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/odmzaM/">odmzaM</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

The next re-render occurs when the `setTimeout()` is invoked and `this.forceUpdate()` is called. Note that simply updating the state (i.e. `this.state.now = 'foo'`;) does not cause a re-render. I set the state using `this.state`, and then I have to call `this.forceUpdate()` so the component will re-render with the new state.