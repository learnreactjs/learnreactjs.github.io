---
title: "Accessing Children Components/Nodes"
permalink: /access-child-component-node
excerpt: "Accessing Children Components/Nodes - Learn React"
last_modified_at: 2018-05-19T15:58:49-04:00
---

If a component contains child React components. or React nodes inside of the component (e.g. `<Parent><Child /></Parent>` or `<Parent><span>test<span></Parent>`). these React node or component instances can be accessed by using this.props.children.

In the example below the `FirstParent` component contains two `<div>` React node children, which contains React text nodes. 

All of the children instances, inside of the component are accessible using `this.props.children`. In the example below I access these children inside of the `FirstParent componentDidMount` lifecycle function.

<p data-height="265" data-theme-id="dark" data-slug-hash="gzqYyg" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="gzqYyg" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/gzqYyg/">gzqYyg</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

The `this.props.children` of the `FirstParent` component instance returns an array containing the references to the child React node instances. This array is logged out to the console. Additionally, in the `FirstParent` component I am logging out the child of the first <div> (i.e., a text node).

When I use the `SecondParent` component inside of the `FirstParent` component the child React node of `SecondParent` only contains one `<span>` React node (i.e. <span>child2text</span>). Thus, `this.props.children` used in `componentDidMount` lifecycle method for `SecondParent` component will be a direct reference to this `<span>` React node (i.e. not an array containing a single reference).

Given that `this.props.children` can potentially contain a wide set of nodes and components React provides a set of utilities to deal with this data structure. 

These utilities are listed below:

| Utilitie        | Description           |
|:----------------|:----------------------|
| React.Children.map(this.props.children, function() {}) | Invoke fn on every immediate child contained within children with this set to thisArg. If children is a keyed fragment or array it will be traversed: fn will never be passed the container objects. If children is null or undefined returns null or undefined rather than an array. |
| React.Children.forEach(this.props.children, function() {}) | Like React.Children.map() but does not return an array. |
| React.Children.count(this.props.children) | Return the total number of components in children, equal to the number of times that a callback passed to map or forEach would be invoked. |
| React.Children.only(this.props.children) | Return the only child in children. Throws otherwise. |
| React.Children.toArray(this.props.children) | Return the children opaque data structure as a flat array with keys assigned to each child. Useful if you want to manipulate collections of children in your render methods, especially if you want to reorder or slice this.props.children before passing it down. |

Note:

* When there is only a single child, `this.props.children` will be the single child component itself without the array wrapper. This saves an array allocation.

