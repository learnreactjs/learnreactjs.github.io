---
title: "Defining Node Attributes/Props"
permalink: /define-node-attributes-and-props
excerpt: "Defining Node Attributes/Props - Learn React"
last_modified_at: 2018-05-16T15:58:49-04:00
---

The second argument that is passed to `React.createElement(type, props, children)` is an object containing name value properties (props).

Props has several roles:

* Props can become HTML attributes. If a prop matches a known HTML attribute then it will be added to the final HTML element in the DOM.
* Props passed to `createElement()` become values stored in a `prop` object as an instance property of `React.createElement()` instances (i.e. `[INSTANCE].props.[NAME OF PROP]`). Props are normally used to input values into components.
* A few special props have side effects (e.g. `key`, `ref`).

You can think of props as the configuration options for React nodes or you can think of them as HTML attributes.

In the example below I am defining a React `<option>` element node with five props. One is a non-standard HTML attribute (i.e. foo:'bar') and the others are known HTML attributes.

```
var reactNodeOption = React.createElement('option',
  {
    foo: 'bar',
    // Note the use of the JS className property to change the 
    // class attribute below
    className: 'one',
    'data-test': 'test',
    'aria-role' :'optionitem',
    // Note use of JS camel-cased CSS property backgroundColor below
    style: {backgroundColor: 'red'}
  },
  'one'
);
```

Once the above code is rendered to an HTML page the HTML created will look like:

```
<li data-test="test" class="one" aria-role="optionitem" style="background-color: red;" data-reactid=".0">one</li>
```

What you need to realize is only the following attributes get passed to the real DOM from the Virtual DOM:

* [Standard HTML attributes](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes)
* [Custom data attributes data-*](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes)
* [Accessibility attributes aria-*](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA)

The `foo` attribute/prop does not show up in the real DOM. This non-standard HTML attribute is available as an instance property of the created `option` React node instance. (e.g. `reactNodeOption.props.foo`).

<p data-height="265" data-theme-id="dark" data-slug-hash="LmJGdY" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="LmJGdY" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/LmJGdY/">LmJGdY</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

React attributes/props not only translate to real HTML attributes props, they become configuration values that are passed to React components. This aspect of props will be covered in the React component props chapter. For now simply realize that passing a prop into a React node is different from defining a prop on a component to be used as configuration input within a component.
