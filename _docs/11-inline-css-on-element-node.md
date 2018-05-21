---
title: "Inlining CSS on Element Nodes"
permalink: /inline-css-on-element-node
excerpt: "Inlining CSS on Element Nodes - Learn React"
last_modified_at: 2018-05-16T15:58:49-04:00
---

To apply inline CSS to a React node you have to pass a `style` attribute/prop with an object value containing CSS properties and values.

For the example below I am passing a style prop referencing (i.e. inlineStyle) an object containing CSS properties and values:

```
var inlineStyles = {backgroundColor: 'red', fontSize: 20};

var reactNodeOption =  React.createElement('div', {style: inlineStyles}, 'styled')

ReactDOM.render(reactNodeOption, document.getElementById('app'));
```

The resulting HTML will look like:

```
<div id="app">
  <div style="background-color: red; font-size: 20px;" data-reactid=".0">styled</div>
</div>
```

Note two things in the JavaScript code above:

* I didn't have to add the "px" to the fontSize value because React did it for me.
* When writing CSS properties in JavaScript you have to use the [camelCased version of the CSS property](https://www.w3.org/TR/DOM-Level-2-Style/css.html#CSS-ElementCSSInlineStyle) (e.g. `backgroundColor` not `background-color`).
