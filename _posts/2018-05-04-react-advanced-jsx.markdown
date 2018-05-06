---
layout: post
title: React - Advanced JSX
date: 2018-05-04
description: React Advanced JSX
img: react-advanced-jsx.png
tags: [react, reactjs, learn react]
---

Let’s get started and learn deeply with JSX.

## Embedding Expressions in JSX

You can embed any [JavaScript expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Expressions) in JSX by wrapping it in curly braces; for example `2 + 2`, `user.firstName`, and `formatName(user)` are all valid expressions:

```javascript
function formatName(user) {
  return user.firstName + ' ' + user.lastName;
}

const user = {
  firstName: 'Brian',
  lastName: 'Van'
};

const element = (
  <h1>
    Hello, {formatName(user)}!
  </h1>
);

ReactDOM.render(
  element,
  document.body
);
```

[Try it on CodePen](https://codepen.io/Bunlong/pen/RyLQMg).

## JSX with Expression

you can use JSX inside of `if` statements and `for loops`, assign it to variables, accept it as arguments, and return it from functions:

```javascript
function getName(user) {
  if (user) {
    return <h1>Hello, {formatName(user)}!</h1>;
  }

  return <h1>Hello, Stranger.</h1>;
}
```

## Attributes with JSX

You may use quotes to specify string literals as attributes:

```javascript
const element = <div tabIndex="0"></div>;
```

You may also use curly braces to embed a JavaScript expression in an attribute:

```javascript
const element = <img src={user.avatarUrl}></img>;
```

***Noted:***

Since JSX is closer to JavaScript than to HTML, React DOM uses camelCase property naming convention instead of HTML attribute names.

For example, `class` becomes `className` in JSX, and `tabindex` becomes `tabIndex` but `id` keep the same.

## Children with JSX

If a tag is empty, you may close it immediately with />, like XML:

```javascript
const element = <img src={user.avatarUrl} />;
```

JSX tags may contain children:

```javascript
const element = (
  <div>
    <h1>Hello!</h1>
    <h2>Good to see you here.</h2>
  </div>
);
```