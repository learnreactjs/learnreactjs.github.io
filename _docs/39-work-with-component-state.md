---
title: "Working with Component State"
permalink: /work-with-component-state
excerpt: "Working with Component State - Learn React"
last_modified_at: 2018-05-20T15:58:49-04:00
---

Working with component state typically involves setting a components default state, accessing the current state, and updating the state.

In the example below I am creating a `<MyComponent />` that demonstrates the use of `this.state=...`, `this.state.[STATE]`, and `this.setState()`. If you click on the component in a web browser (i.e. the face) then it will cycle through the states (i.e. moods) available. Thus, the component has three potential states, tied to the UI, based on clicks from the UI user. Go ahead and click on the face in the results tab below.

<p data-height="265" data-theme-id="dark" data-slug-hash="QrYQVM" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="QrYQVM" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/QrYQVM/">QrYQVM</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

Note that the `<MyComponent />` has an initial state of `':|'`, that is set using `this.state = {mood: ':|'};`, which is used in the component when it is first rendered by writing, `{this.state.mood}`.

To change the state, an event listener is added; in this case a click event (i.e. `onClick`) on the `<span>` node that will call the `changeMood` function. Within this function I use `this.setState()` to cycle to the next mood based on the current mood/state. After the state is update (i.e. `setState()` merges the changes) the component will re-render itself and the UI will change.

Things to keep in mind about React component state:

* If a component has state, a default state should be provided using `this.state=...`.
* The only way a component should have its state update should be by using `this.setState()`. While other ways are possible (i.e. `forceUpdate()`), they should likely not be used (except maybe when integrating with third-party solutions).
* You inform a component of a state change by using this.setState() to set a new state. This will result in re-render of the component and all children components that need re-rendered.
* A state change merges new data with old data that is already contained in the state. But this is only a shallow update/merge, it won't do a deep update/merge.
* A state change internally deals with calling re-renders. You should never have to call `this.render()` directly.
* The state object should only contain the minimal amount of data needed for the UI. Don't place computed data, other React components, or props in the state object.