---
layout: post
title: React - Props and PropTypes
date: 2018-05-05
description: 
img: react-props-and-proptypes.png
tags: [react, reactjs, learn react]
---

## Props

React is built around the concept of components. The components get many specific attributes just like a XML syntax and HTML tag does.

The attributes are called "props" in ReactJS and can be of any type. It can be a string, function or an Array, as long as its valid javascript you can use it as a prop.

```javascript
<MyComponent size={24} position="fixed" />
```
`Size & position` is props made up by `MyComponent` component. Using anything other than a string you need to wrap your props in {}.

## PropTypes

PropTypes defines type and which props are required. This benefits the future you using your component in two ways:

1. You can easily open up a component and check which props are required and what type they should be.

2. When things get messed up React will give you an awesome error message in the console, saying which props is wrong/missing plus the render method that caused the problem.

### Installation

propTypes can be used directly from the Facebook CDN by including the link below in header tag:

```javascript
<!-- development version -->
<script src="https://unpkg.com/prop-types@15.6/prop-types.js"></script>
 
<!-- production version -->
<script src="https://unpkg.com/prop-types@15.6/prop-types.min.js"></script>
```

But I would like to recommend using [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/lang/en/) for managing front-end dependencies.

To install `prop-types` with Yarn, run in the terminal:

```javascript
npm install prop-types --save
```

### Usage

So how do we write the propTypes?

```javascript
propTypes = {
  size: PropTypes.number,
  position: PropTypes.string.isRequired
}
```

And more awesome, if we can’t find a propTypes that suits our needs we can write own with regex or shapes:

```javascript
propTypes = {
  email: function(props, propName, componentName) {
    if (!/emailRegex/.test(props[email])) {
      return new Error('Give me a real email!');
    }
  },
  user: PropTypes.shape({
    name: PropTypes.string.isRequired,
    age: PropTypes.number
  }).isRequired
}
```

Exercises:

```javascript
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Learn React</title>
    <script crossorigin src="https://unpkg.com/react@16/umd/react.production.min.js"></script>
    <script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.production.min.js"></script>
    <script crossorigin src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
    <script src="https://unpkg.com/prop-types@15.6/prop-types.js"></script>
  </head>
  <body>
    <script type="text/jsx">
      class Profile extends React.Component {
        constructor(props) {
          super(props)
          this.state = {
            name: 'This is a default prop',
            age: 0,
            activate: true
          }
        }
        
        render() {
          return ( 
            <div>
              <h1>Name: {this.props.name}</h1>
              <h1>Age: {this.props.age}</h1>
              <h1>Activate: {this.props.activate}</h1>
            </div>
          );
        }
      }

      Profile.propTypes = {
        name: PropTypes.string,
        age: PropTypes.number,
        activate: PropTypes.bool
      }

      Profile.defaultProps = {
        name: 'Ryan',
        age: 30,
        activate: false
      }

      ReactDOM.render(
        <Profile />,
        document.body
      );
    </script>
  </body>
</html>
```

[Try it on CodePen](https://codepen.io/Bunlong/pen/GdMQYO).