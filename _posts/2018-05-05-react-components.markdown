---
layout: post
title: React - Components
date: 2018-05-04
description: Components let you split the UI into independent, reusable pieces. Components are like JavaScript functions; they accept inputs called `props` and return React elements.
img: react-components.png
tags: [react, reactjs, learn react]
---

Components let you split the UI into independent, reusable pieces. Components are like JavaScript functions; they accept inputs called `props` and return React elements.


## Functional Components

You can define a component using JavaScript function:

```javascript
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

This function is a React component because it accepts a single "props" object argument and returns a React element. We call such components "functional components" because they are literally JavaScript functions.

## Class Components

You can also use an ES6 class to define a component:

```javascript
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

The above components is class components.

## Rendering a Component

let take a look the elements; React elements represent DOM tags:

```javascript
const element = <div />;
```

And React elements also represent user defined componets:

```javascript
const element = <Welcome name="Brian" />;
```

Once React sees an element representing a user-defined component, it passes JSX attributes to this component as a single object. We call this object `props`.

For example, the below code renders "Hello, Brian" on the page:

```javascript
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

const element = <Welcome name="Brian" />;

ReactDOM.render(
  element,
  document.getElementById('root')
);
```

Let’s take a look what happens in this example:

1. We call `ReactDOM.render()` with the `<Welcome name="Brian" />` element.

2. React calls the `Welcome` component with `{name: 'Brian'}` as the props.

3. Our `Welcome` component returns a `<h1>Hello, Sara</h1>` element as the result.

4. React DOM efficiently updates the DOM to match `<h1>Hello, Sara</h1>`.

Noted: 

***Always start component names with a capital letter.***

React treats components starting with lowercase letters as DOM tags. For example, `<div />` represents an HTML div tag, but `<Welcome />` represents a component and requires Welcome to be in scope.

## Composing Components

Components can be in other components in order to output. This lets us use the same component for any level of detail. 

A button, a form, a dialog, a screen: in React apps, all those are commonly expressed as components.

For example below, we can create an `App` component that renders `Welcome` many times:

```javascript
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

function App() {
  return (
    <div>
      <Welcome name="Brian" />
      <Welcome name="Ryan" />
    </div>
  );
}

ReactDOM.render(
  <App />,
  document.getElementById('root')
);
```

## Extracting Components

When components is nested don’t be afraid to split components into smaller components.

For example, consider this `Comment` component:

```javascript
function Comment(props) {
  return (
    <div className="Comment">
      <div className="UserInfo">
        <img className="Avatar"
          src={props.author.avatarUrl}
          alt={props.author.name}
        />
        <div className="UserInfo-name">
          {props.author.name}
        </div>
      </div>
      <div className="Comment-text">
        {props.text}
      </div>
      <div className="Comment-date">
        {formatDate(props.date)}
      </div>
    </div>
  );
}
```

It accepts author (an object), text (a string), and date (a date) as props, and describes a comment on a social media website.

Well, this component can be tricky to change because of all the nesting, and it is also hard to reuse individual parts of it. Let’s extract a few components.

First, we will extract `Avatar`:

```javascript
function Avatar(props) {
  return (
    <img className="Avatar"
      src={props.user.avatarUrl}
      alt={props.user.name}
    />

  );
}
```

The Avatar doesn't need to know that it is being rendered inside a Comment. That why we have given its prop a more generic name: user rather than author.

We can now simplify Comment a tiny bit:

```javascript
function Comment(props) {
  return (
    <div className="Comment">
      <div className="UserInfo">
        <Avatar user={props.author} />
        <div className="UserInfo-name">
          {props.author.name}
        </div>
      </div>
      <div className="Comment-text">
        {props.text}
      </div>
      <div className="Comment-date">
        {formatDate(props.date)}
      </div>
    </div>
  );
}
```

Next, we will extract a `UserInfo` component that renders an `Avatar` next to the user's name:

```javascript
function UserInfo(props) {
  return (
    <div className="UserInfo">
      <Avatar user={props.user} />
      <div className="UserInfo-name">
        {props.user.name}
      </div>
    </div>
  );
}
```

This lets us simplify Comment even better:

```javascript
function Comment(props) {
  return (
    <div className="Comment">
      <UserInfo user={props.author} />
      <div className="Comment-text">
        {props.text}
      </div>
      <div className="Comment-date">
        {formatDate(props.date)}
      </div>
    </div>
  );
}
```

Extracting components is reusable components pays off in larger apps. if a part of your UI is used several times (Button, Panel, Avatar), or is complex enough on its own (App, FeedStory, Comment), it is a good candidate to be a reusable component.
