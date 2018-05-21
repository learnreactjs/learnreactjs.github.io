---
title: "State Vs Props"
permalink: /state-vs-props
excerpt: "State Vs Props - Learn React"
last_modified_at: 2018-05-21T15:58:49-04:00
---

A components `state` and `props` do share some points:

* Both are plain JS objects
* Both can have default values
* Both should be accessed/read via `this.props` or `this.state`, but neither should be given values this way. i.e. both are readonly when using this.

However they are used for different reasons and in different ways:

Props:

* Props are passed into a component from above, either a parent component or from the starting scope where React is originally rendered.
* Props are intended as configuration values passed into the component. Think of them like arguments passed into a function (If you don't use JSX that is exactly what they are).
* Props are immutable to the component receiving them. i.e. don't change props passed to a component from within the component.

State:

* State is a serializable representation of data (a JS object) at one point in time that typically is tied to UI.
* State should always start with a default value and then the state is mutated internally by the component using `setState()`.
* State can only be mutated by the component that contains the state. It is private in this sense.
* Don't mutate the state of child components. A component should never have shared mutable state.
* State should only contain the minimal amount of data needed to represent your UI's state. It should not contain computed data, other React components, or duplicated data from props.
* State should be avoided if at all possible. i.e., stateless components are ideal, stateful components add complexity. The React documentation suggest: "A common pattern is to create several stateless components that just render data, and have a stateful component above them in the hierarchy that passes its state to its children via props. The stateful component encapsulates all of the interaction logic, while the stateless components take care of rendering data in a declarative way."
