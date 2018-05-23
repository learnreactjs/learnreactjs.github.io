---
title: "What is Controlled Component?"
permalink: /what-is-controlled-component
excerpt: "What is Controlled Component? - Learn React"
last_modified_at: 2018-05-23T15:58:49-04:00
---

A Controlled Component is one that takes its current value through state and notifies changes through callbacks like `onChange`.

For example below, I log the name when it is submitted, with controlled component:

<p data-height="265" data-theme-id="0" data-slug-hash="pVBwwa" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="pVBwwa" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/pVBwwa/">pVBwwa</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

`<input>` form element takes its current value through `this.state.value`. `handleChange` runs on every keystroke to update `this.state.value`, the displayed value will update as the user types.
