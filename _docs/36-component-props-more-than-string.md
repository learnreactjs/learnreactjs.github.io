---
title: "Component Props More Than Strings"
permalink: /component-props-more-than-string
excerpt: "Component Props More Than Strings - Learn React"
last_modified_at: 2018-05-20T15:58:49-04:00
---

Before looking at validating props one needs to make sure they understand that a component prop can be any valid JavaScript value.

In the example below I setup several default props containing several different JavaScript values.

<p data-height="265" data-theme-id="dark" data-slug-hash="qYgpqX" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="qYgpqX" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/qYgpqX/">qYgpqX</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

Note how the `propArray` and `propObject` were overwritten with new values when the `MyComponent` instance is created.

The main take away here is that you are not limited to string values when passing prop values.
