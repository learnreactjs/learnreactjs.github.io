---
title: "Setting Default Value"
permalink: /set-default-value-uncontrolled-component
excerpt: "Setting Default Value Uncontrolled Component - Learn React"
last_modified_at: 2018-05-23T15:58:49-04:00
---

In the React rendering lifecycle, the value attribute on form elements will override the value in the DOM. 

But with an uncontrolled component, to handle this case, you can specify a `defaultValue` attribute instead of value.

For example below, I use `defaultValue` attribute to set default value of `<input>` form element:

<p data-height="265" data-theme-id="0" data-slug-hash="rvgGrm" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="rvgGrm" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/rvgGrm/">rvgGrm</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

Note:

* `<input type="checkbox">` and `<input type="radio">` support `defaultChecked`.
* `<select>` and `<textarea>` supports `defaultValue`.
