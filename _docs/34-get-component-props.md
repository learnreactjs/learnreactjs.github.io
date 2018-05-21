---
title: "Getting Component Props"
permalink: /get-component-props
excerpt: "Getting Component Props - Learn React"
last_modified_at: 2018-05-20T15:58:49-04:00
---

As discussed in section [Mentioning to a Component Instance](/mention-to-a-component-instance) a component instance can be accessed from any lifecycle methods by way of the `this` keyword. For example, in the example below the `this` keyword is used to access the `MyComponent` props from the component `render()` method (i.e. this.props.name).

```javascript
ReactDOM.render(<Badge name="Bill" />, document.getElementById('app'));

class MyComponent extends React.Component {
  render() {
    return <div>{this.props.name}</div>;
  }
}

ReactDOM.render(
  <MyComponent name="Brian" />, 
  document.getElementById('app')
);
```

If you look at the transformed JavaScript (i.e. JSX to JS):

```javascript
var MyComponent = createReactClass({
    displayName: "MyComponent",
    render: function render() {
      return React.createElement(
        "div",
        null,
        this.props.name
      );
    }
});

ReactDOM.render(
  React.createElement(MyComponent, { name: "Brian" }), 
  document.getElementById('app')
);
```

The `{ name: "Brian" }` object is sent to the `createElement()` function along with a reference to the `MyComponent` component. The value `{ name: "Brian" }` is set as an instance property value of the component accessible from the props property (ie. this.props.name === "Brian").

Note:

* You should consider `this.props` to be readonly.