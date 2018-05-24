---
title: "What is Uncontrolled Component?"
permalink: /what-is-uncontrolled-component
excerpt: "What is Uncontrolled Component? - Learn React"
last_modified_at: 2018-05-23T15:58:49-04:00
---

A Uncontrolled Component is one that stores its own state internally, and you query the DOM using a `ref` to find its current value when you need it. This is a bit more like traditional HTML.

For the example below, this code accepts a single name in an uncontrolled component:

<p data-height="265" data-theme-id="0" data-slug-hash="RympZV" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="RympZV" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/RympZV/">RympZV</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

`<input>` query the DOM using a `ref`, stores the DOM in its own state `this.input`, and find it's current value using `this.input.value`.

Since an uncontrolled component keeps the source in the DOM, it is sometimes easier to integrate React and non-React code when using uncontrolled components.

If it's still not clear which type of component you should use for a particular situation, you might find [this article on controlled versus uncontrolled inputs](https://goshakkk.name/controlled-vs-uncontrolled-inputs-react) to be helpful.
