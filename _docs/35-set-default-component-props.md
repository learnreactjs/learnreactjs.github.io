---
title: "Setting Default Component Props"
permalink: /set-default-component-props
excerpt: "Setting Default Component Props - Learn React"
last_modified_at: 2018-05-20T15:58:49-04:00
---

Default props can be set when a component is being defined by using PropTypes [prop-types](https://www.npmjs.com/package/prop-types) modules or [prop-types.js](https://unpkg.com/prop-types@15.6/prop-types.js) file.

PropTypes defines type and which props are required. This benefits the future you using your component in two ways:

* You can easily open up a component and check which props are required and what type they should be.
* When things get messed up React will give you an awesome error message in the console, saying which props is wrong/missing plus the render method that caused the problem.

## Usage

In the example below we define `props` type and validation:

```javascript
class MyComponent extends React.Component {
  render() {
    // ... Do things with the props
  }
}

MyComponent.propTypes = {
  name: PropTypes.string,
  age: PropTypes.number.isRequired,
}

MyComponent.defaultProps = {
  name: 'Brian',
  age: 30
}
```

And more awesome, if we can't find a propTypes that suits our needs we can write own with regex or shapes:

```javascript
MyComponent.propTypes = {
  email: function(props, propName, componentName) {
    if (!/emailRegex/.test(props[email])) {
      return new Error('Give me a real email!');
    }
  },
}
```

In the example below, the `MyComponent` component has a default value for the `name` prop.

<p data-height="265" data-theme-id="dark" data-slug-hash="deaJYV" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="deaJYV" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/deaJYV/">deaJYV</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

Default props will be set on `this.props` if no prop is sent into the component.

Note:

* The `defaultProps` is invoked once and cached when the component is created.
* The `defaultProps` is run before any instances are created.
* Any objects returned by `defaultProps` will be shared across instances, not copied.
