---
title: "Validating Component Props"
permalink: /validate-component-props
excerpt: "Validating Component Props - Learn React"
last_modified_at: 2018-05-20T15:58:49-04:00
---

`props` can be validated when component instances are created.

When defining a component, the `propTypes` configuration option can be used to identify if and how props should be validated. 

In the example below I'm checking to see that `propArray` and `propFunc` are in fact the correct data types and are sent into the component when it is instantiated:

<p data-height="265" data-theme-id="dark" data-slug-hash="NMoXwQ" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="NMoXwQ" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/NMoXwQ/">NMoXwQ</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

I am not sending the correct props as specified using `propTypes` to demonstrate that doing so will cause an error. The above code will result in the following error showing up in the console.

```
"Warning: Failed prop type: Invalid prop `propArray` of type `object` supplied to `MyComponent`, expected `array`.
    in MyComponent"

"Warning: Failed prop type: The prop `propFunc` is marked as required in `MyComponent`, but its value is `undefined`.
    in MyComponent"
```

Note however, the commented below will not cause an error:

```
ReactDOM.render(<MyComponent propArray={[1,2]} propFunc={function(){return 3;}} />, document.getElementById('app'));
```

React offers several built in validators (e.g. `PropTypes[VALIDATOR]`) which I outline below (Note that creating custom validators are possible as well.):

## Basic type validators

These validators check to see if the prop is a specific JS primitive. By default all these are optional. In other words, the validation only occurs if the prop is set.

| Type          | Description   |
|:--------------|:--------------|
| PropTypes.string | If prop is used, verify it is a string |
| PropTypes.bool | If prop is used, verify it is a boolean |
| PropTypes.func | If prop is used, verify it is a function |
| PropTypes.number | If prop is used, verify it is a number |
| PropTypes.object | If prop is used, verify it is a object |
| PropTypes.array | If prop is used, verify it is a array |
| PropTypes.any | If prop is used, verify it is of any type |

## Required type validators

| Type          | Description   |
|:--------------|:--------------|
| PropTypes.[TYPE].isRequired | Chaining the .isRequired on to any type validation to make sure the prop is provided (e.g. propTypes: {propFunc:React.PropTypes.func.isRequired} ) |

## Element validators

| Type          | Description   |
|:--------------|:--------------|
| PropTypes.element | Is a React element. |
| PropTypes.node | Is anything that can be rendered: numbers, strings, elements or an array (or fragment) containing these types. |

## Enumerables validators

| Type          | Description   |
|:--------------|:--------------|
| React.PropTypes.oneOf(['Mon','Fri']) | Is one of several types of specific values. |
| React.PropTypes.oneOfType([React.PropTypes.string,React.PropTypes.number]) | Is an object that could be one of many types. |

## Array and Object validators

| Type          | Description   |
|:--------------|:--------------|
| React.PropTypes.arrayOf(React.PropTypes.number) | Is an array containing only one type of values. |
| React.PropTypes.objectOf(React.PropTypes.number) | Is an object containing only one type of property values |
| React.PropTypes.instanceOf(People) | Is object instance of specific constructor(uses `instanceof`) |
| React.PropTypes.shape({color:React.PropTypes.string,size: React.PropTypes.number}) | Is object containing properties having a specific type |

## Custom validators

| Type          | Description   |
|:--------------|:--------------|
| function(props, propName, componentName) {} | propTypes: { customProp: function(props, propName, componentName) { if (!/matchme/.test(props[propName])) { return new Error('Validation failed!'); }}} |
