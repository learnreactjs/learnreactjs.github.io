---
layout: post
title: React - Component Lifecycle Mounting
date: 2018-05-08
description: 
img: react-component-lifecycle-updating.png
tags: [react, reactjs, learn react]
---

React updating have 5 methods: 

* UNSAFE_componentWillReceiveProps(object nextProps)

* shouldComponentUpdate(object nextProps, object nextState)

* UNSAFE_componentWillUpdate(object nextProps, object nextState)

* componentDidUpdate(object prevProps, object prevState, object snapshot)

* getSnapshotBeforeUpdate(object prevProps, object prevState).

Let go into details:

#### UNSAFE_componentWillReceiveProps

is invoked before a mounted component receives new props. If you need to update the state in response to prop changes (for example, to reset it), you may compare `this.props` and `nextProps` and perform state transitions using `this.setState()` in this method.

If a parent component causes your component to re-render, this method will be called even if props have not changed. Make sure to compare the current and next values if you only want to handle changes.

React doesn’t call UNSAFE_componentWillReceiveProps() with initial props during mounting. It only calls this method if some of component’s props may update. Calling this.setState() generally doesn’t trigger UNSAFE_componentWillReceiveProps().

#### shouldComponentUpdate(object nextProps, object nextState) boolean

Use `shouldComponentUpdate()` to let React know if a component's output is not affected by the current change in state or props.

is invoked before rendering when new props or state are being received. Defaults to `true`. This method is not called for the initial render or when forceUpdate() is used.

This method return true by default.

Returning false does not prevent child components from re-rendering when their state changes.

If shouldComponentUpdate() returns false, then UNSAFE_componentWillUpdate(), render(), and componentDidUpdate() will not be invoked.

If you determine a component is slow after profiling, you may change it to inherit from `React.PureComponent` which implements shouldComponentUpdate() with a shallow prop and state comparison.

#### UNSAFE_componentWillUpdate(object nextProps, object nextState)

is invoked just before rendering when new props or state are being received. Use this to perform preparation before an update occurs. This method is not called for the initial render.

You cannot call this.setState() here in this method.

You should do anything else in this method (e.g. dispatch a Redux action) that would trigger an update to a React component before `UNSAFE_componentWillUpdate()` returns.

#### componentDidUpdate(object prevProps, object prevState, object snapshot)

is invoked immediately after updating occurs. This method is not called for the initial render.

Use this as an opportunity to operate on the DOM when the component has been updated. This is also a good place to do network requests as long as you compare the current props to previous props (e.g. a network request may not be necessary if the props have not changed).

If your component implements the `getSnapshotBeforeUpdate()` lifecycle, the value it returns will be passed as a third “snapshot” parameter to `componentDidUpdate()`. (Otherwise this parameter will be undefined.)

Noted: `componentDidUpdate()` will not be invoked if shouldComponentUpdate() returns false.

#### getSnapshotBeforeUpdate(object prevProps, object prevState)

is invoked right before the most recently rendered output is committed to e.g. the DOM. It enables your component to capture current values (e.g. scroll position) before they are potentially changed. Any value returned by this lifecycle will be passed as a parameter to `componentDidUpdate()`.

For example:

```javascript
class ScrollingList extends React.Component {
  constructor(props) {
    super(props);
    this.listRef = React.createRef();
  }

  getSnapshotBeforeUpdate(prevProps, prevState) {
    // Are we adding new items to the list?
    // Capture the scroll position so we can adjust scroll later.
    if (prevProps.list.length < this.props.list.length) {
      const list = this.listRef.current;
      return list.scrollHeight - list.scrollTop;
    }
    return null;
  }

  componentDidUpdate(prevProps, prevState, snapshot) {
    // If we have a snapshot value, we've just added new items.
    // Adjust scroll so these new items don't push the old ones out of view.
    // (snapshot here is the value returned from getSnapshotBeforeUpdate)
    if (snapshot !== null) {
      const list = this.listRef.current;
      list.scrollTop = list.scrollHeight - snapshot;
    }
  }

  render() {
    return (
      <div ref={this.listRef}>{/* ...contents... */}</div>
    );
  }
}
```

In the above examples, it is important to read the `scrollHeight` property in `getSnapshotBeforeUpdate` rather than `componentWillUpdate` in order to support async rendering. With async rendering, there may be delays between “render” phase lifecycles (like `componentWillUpdate` and render) and “commit” phase lifecycles (like `getSnapshotBeforeUpdate` and `componentDidUpdate`). If a user does something like resize the browser during this time, a `scrollHeight` value read from `componentWillUpdate` will be stale.