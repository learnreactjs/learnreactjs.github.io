---
title: "Using react and react-dom in an HTML Page"
permalink: /react-set-up-react-and-react-dom
excerpt: "Using react and react-dom in an HTML Page - Learn React"
last_modified_at: 2018-05-14T15:58:49-04:00
---

The `react.js` file is the core file needed to create React elements and write react components.

When you intend to render your components in an HTML document (i.e., the DOM) you'll also need the `react-dom.js` file.

A React component is created by calling `createReactClass()` (or, React.Component if using ES6 classes). React.createClass is deprecated, `create-react-class` is available on npm. To use `createReactClass()` you need to include `create-react-class` file.

An example of an HTML document properly including React is shown below.

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Learn React</title>
    <script crossorigin src="https://unpkg.com/react@16/umd/react.production.min.js"></script>
    <script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.production.min.js"></script>
    <script crossorigin src="https://unpkg.com/create-react-class@15.6.0-rc.0/create-react-class.min.js"></script>
  </head>
  <body>
  </body>
</html>
```

With the `react js` file and `react-dom js` file loaded into an HTML page it is then possible to create React nodes/components and then render them to the DOM. In the HTML below a `HelloMessage` React component is created containing a React `<div>` node that is rendered to the DOM inside of the `<div id="app"></div>` HTML element.

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Learn React</title>
    <script crossorigin src="https://unpkg.com/react@16/umd/react.production.min.js"></script>
    <script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.production.min.js"></script>
    <script crossorigin src="https://unpkg.com/create-react-class@15.6.0-rc.0/create-react-class.min.js"></script>
  </head>
  <body>
    <div id="app"></div>
    <script>
      var HelloMessage = createReactClass({
        displayName: 'HelloMessage',
        render: function render() {
          return React.createElement('div', null, 'Hello ', this.props.name);
        }
      });

      ReactDOM.render(
        React.createElement(HelloMessage, { name: 'Brian' }), 
        document.getElementById('app')
      );
    </script>
  </body>
</html>
```

This setup is all you need to use React. However this setup does not make use of JSX. The next section we will discuss about JSX usage.

**Note:** Don't make the `<body>` element the root node for your React app. Always put a root `<div>` into `<body>`, give it an ID, and render into it. This gives React its own pool to play in without worrying about what else potentially wants to make changes to the children of the `<body>` element.
{: .notice--warning}