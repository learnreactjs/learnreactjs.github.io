---
title: "What is Component Props?"
permalink: /what-is-component-props
excerpt: "What is Component Props? - Learn React"
last_modified_at: 2018-05-20T15:58:49-04:00
---

Props is similar to HTML attributes. In other words, props provide configuration values for the component. 

In the example below a MyComponent is created and it is expecting a 'name' prop to be sent when the component is instantiated:

<p data-height="265" data-theme-id="dark" data-slug-hash="yjZVJo" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="yjZVJo" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/yjZVJo/">yjZVJo</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

Inside the render function of the `<App>` component, where `<MyComponent>` is used, the name prop is added to the `<MyComponent>` component much like an HTML attribute is added to an HTML element (i.e. `<MyComponent name="Brian" />`). The name prop is then used by the `MyComponent` component (i.e. `this.props.name`) as the text node for the React `<div>` node rendered by the `MyComponent` component. This is similar to how an `<input>` can take a value attribute which it uses to display a value.

the `App` component uses two `MyComponent` components each with their own `this.props` object. We can verify this by console logging out the value of `this.props` when a `MyComponent` component is instantiated.

Basically every React component instance has a unique instance property called props that starts as an empty JavaScript object. The empty object can get filled, by a parent component, with any JavaScript value/reference. These values are then used by the component or passed on to child components.

Note:
  * You should consider `this.props` to be readonly.
