---
title: "Select"
permalink: /select-controlled-componet
excerpt: "React Forms Select Controlled Component - Learn React"
last_modified_at: 2018-05-23T15:58:49-04:00
---

In HTML, `<select>` form element creates a drop-down list.

```javascript
<select>
  <option value="papaya">Papaya</option>
  <option value="orange">Orange</option>
  <option selected value="coconut">Coconut</option>
</select>
```

Note that the Coconut option is selected by default, because of the selected attribute. React, instead of using this selected attribute, uses a value attribute on the root select tag. This is more convenient in a controlled component because you only need to update it in one place.

<p data-height="265" data-theme-id="0" data-slug-hash="OZGvRX" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="OZGvRX" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/OZGvRX/">OZGvRX</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

Note:

You can pass an array into the value attribute, allowing you to select multiple options in a select form element.

```javascript
<select multiple={true} value={['B', 'C']}>
```
