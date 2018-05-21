---
title: "Creating React Nodes With JSX"
permalink: /create-react-node-with-jsx
excerpt: "Creating React Nodes With JSX - Learn React"
last_modified_at: 2018-05-18T15:58:49-04:00
---

Go through the previous chapter you should be familiar with creating React nodes using the `React.createElement()` function. Below I use this familiar function to create one React nodes:

```javascript
//React node, which represents an actual HTML DOM node
var HTMLLi = React.createElement('li', {className:'bar'}, 'foo');
```

To use JSX instead (assuming you have Babel setup) of `React.createElement()` to create these React nodes one just has to replace React.createElement() function calls with the HTML/XML like tags which represent the HTML you'd like the virtual DOM to spit out. The above code can be written in JSX like so:

```javascript
//React node, which represents an actual HTML DOM node
var HTMLOption = <option value="1">one</option>;
```

Notice that the JSX is not in a JavaScript string format and can just be writing as if you are writing it inside of an `.html` file.

JSX is transformed back into the `React.createElement()` functions calls by Babel. You can see the transformation below:

<p data-height="265" data-theme-id="dark" data-slug-hash="odJLPe" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="odJLPe" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/odJLPe/">odJLPe</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

HTML produced in the above CodePen it would look like so:

```javascript
<body>
  <div id="app"><option value="1" data-reactid=".0">one</li></div>
</body>
```

Creating React nodes using JSX is as simple as writing HTML like code in your JavaScript files.

Note:

* The `class` attribute has to be written `className`
* The `for` attribute has to be written `htmlFor`
* The style attribute takes an object of [camel-cased style properties](https://www.w3.org/TR/DOM-Level-2-Style/css.html#CSS-CSS2Properties)
* All attributes are camel-cased (e.g. `accept-charset` is written as `acceptCharset`)
