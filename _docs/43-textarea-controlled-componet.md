---
title: "Textarea"
permalink: /textarea-controlled-componet
excerpt: "React Forms Textarea Controlled Component - Learn React"
last_modified_at: 2018-05-23T15:58:49-04:00
---

In HTML, a `<textarea>` form element defines its text by its children.

```javascript
<textarea>
  Some text in a text area
</textarea>
```

In React, a `<textarea>` form element uses a value attribute instead. This way, a form using a `<textarea>` can be written very similarly to a form that uses a `<input>` form element.

<p data-height="265" data-theme-id="0" data-slug-hash="BxEJVq" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="BxEJVq" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/BxEJVq/">BxEJVq</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

Note: `this.state.value` is initialized in the constructor, so that the text area starts off with some text in it.
