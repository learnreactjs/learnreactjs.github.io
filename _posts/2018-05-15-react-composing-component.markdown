---
layout: post
title: React - Composing Component
date: 2018-05-09
description: Components is the best way to reuse code in React.
img: react-composing-component.png
tags: [react, reactjs, learn react]
---

Components is the best way to reuse code in React, React components can make use of other React components. That is, when defining a component the render configuration function can contain references to other components. When a component contains another component it can be said that the parent component owns the child component.

In the code below the BadgeList component contains/owns the BadgeBill and BadgeTom component.

```javascript
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Learn React</title>
    <script crossorigin src="https://unpkg.com/react@16/umd/react.production.min.js"></script>
    <script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.production.min.js"></script>
    <script crossorigin src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
  </head>
  <body>
    <script type="text/jsx">
      class BadgeBill extends React.Component {
        render() {
          return <div>Bill</div>;
        }
      }

      class BadgeTom extends React.Component {
        render() {
          return <div>Tom</div>;
        }
      }

      class BadgeList extends React.Component {
        render() {
          return (
            <div>
              <BadgeBill/>
              <BadgeTom />
            </div>
          );
        }
      }

      ReactDOM.render(<BadgeList />, document.body);
    </script>
  </body>
</html>
```

[Try it on CodePen](https://codepen.io/Bunlong/pen/VxXMEO).