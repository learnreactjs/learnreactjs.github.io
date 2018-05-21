---
title: "Defining Attributes/Props in JSX"
permalink: /define-attribute-props-in-jsx
excerpt: "Defining Attributes/Props in JSX - Learn React"
last_modified_at: 2018-05-19T15:58:49-04:00
---

JSX is used to express XML-like nodes that get turned into HTML, attribute/props are defined by adding the attributes/props to JSX expressions as name-value attributes.

In the example below I am defining a React `<li>` element node, using JSX, with five attributes/props. One is a non-standard HTML attribute and the others are known HTML attributes.

```javascript
var styles = {backgroundColor:'red'};
var tested = true;
var text = 'text';

var reactNodeLi = <li id=""
                      data-test={tested?'test':'false'}
                      className="blue"
                      aria-test="test"
                      style={styles}
                      foo="bar">
                    {text}
                  </li>;

ReactDOM.render(reactNodeLi, document.getElementById('app'));
```

The JSX when it is transformed will look like this (note that attributes/props just become arguments to a function):

```javascript
var reactNodeLi = React.createElement(
  'li',
  { 
    id: '',
    'data-test': tested ? 'test' : 'false',
    className: 'blue',
    'aria-test': 'test',
    style: styles,
    foo: 'bar' 
  },
  text
);

```

When the `reactNodeLi` node is render to the DOM it will look like this:

```javascript
<div id="app1">
  <li id="true"
      data-test="test"
      class="blue"
      aria-test="test"
      style="background-color:red;"
      data-reactid=".0">
    text
  </li>
</div>
```

You should note the following:

* Leaving an attribute/prop blank results in that attribute value becoming true (e.g. `id=""` becomes `id="true"` and test becomes `test="true"`)
* The `foo` attribute, because it was not a standard HTML attribute, doesn't become a final HTML attribute.

Note:

* The `class` attribute has to be written `className`
* The `for` attribute has to be written `htmlFor`
* The `style` attribute takes a reference to an object of [camel-cased style properties](https://www.w3.org/TR/DOM-Level-2-Style/css.html#CSS-CSS2Properties)
* All attributes are camel-cased (e.g. `accept-charset` is written as `acceptCharset`) which differs from how they are written in HTML.
