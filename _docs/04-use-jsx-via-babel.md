---
title: "Using JSX via Babel"
permalink: /use-jsx-via-babel
excerpt: "Using JSX via Babel - Learn React"
last_modified_at: 2018-05-16T15:58:49-04:00
---

The creation of the React `HelloMessage` component and React `<div>` element node in the HTML page below was done using the `createReactClass()` and `React.createElement()` functions. This code should look familiar as it is identical to the HTML from the previous section. This HTML will run without errors in [ES5 browsers](https://kangax.github.io/compat-table/es5/).

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

Optionally, by using JSX via Babel, it is possible to simplify the creation of React elements by abstracting the `React.createElement()` JavaScript function calls so they can be written in a more natural HTML-like style and syntax.

Instead of writing the following, which uses React.createElement():

```
return React.createElement('div', null, 'Hello ', this.props.name);
```

Using JSX, you can write this:

```
return <div>Hello {this.props.name}</div>;
```

And then Babel will convert it back to the code which uses React.createElement() so it can be parsed by a JavaScript engine.

You can consider JSX is a form of HTML that you can directly write in JavaScript that requires a transformation step, done by Babel, into ECMAScript 5 code that browsers can run.

## Transforming JSX via Babel in the Browser

Normally, Babel is setup to automatically process your JavaScript files during development using the Babel CLI tool (e.g., via something like [webpack](https://webpack.github.io)). However, it is possible to use Babel directly in the browser by way of a script include. As we are just getting started we'll avoid CLI tools or learning a module loader to focus on learning React. Note that you should never use this browser transformation in a production environment.

Babel provides the script file (`babel js`) needed to transform JSX code to ES6/ES5 code in the browser.

## Using `babel js` to Transform JSX in the Browser

In the HTML file below the React code we have been working with to create the `HelloMessage` component has been updated to use JSX. The transformation of the code is occurring because we have included the `babel js` file and given the `<script>` element a type attribute of `type="text/babel"`.

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Learn React</title>
    <script crossorigin src="https://unpkg.com/react@16/umd/react.production.min.js"></script>
    <script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.production.min.js"></script>
    <script crossorigin src="https://unpkg.com/create-react-class@15.6.0-rc.0/create-react-class.min.js"></script>
    <script crossorigin src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
  </head>
  <body>
    <div id="app"></div>
    <script type="text/babel">
      var HelloMessage = createReactClass({
        render: function() {
          return <div>Hello {this.props.name}</div>;
        }
      });

      ReactDOM.render(
        <HelloMessage name="Brian" />, 
        document.getElementById('app')
      );
    </script>
  </body>
</html>
```

While transforming JSX in the browser is convenient and easy to setup, it isn't ideal because the transformation cost is occurring at runtime. This will slow down your web pages and may cause memory issues. Therefore using `babel js` is not a production solution.

Note:
* The Babel tool is a [subjective selection](https://reactjs.org/blog/2015/09/10/react-v0.14-rc1.html#compiler-optimizations) from the React team for transforming ES* code and JSX syntax to ES5 code.
* By using JSX:
    * Less technical people can still understand and modify the required parts. CSS developers and designers will find JSX more familiar than JavaScript alone.
    * You can leverage the full power of JavaScript in HTML and avoid learning or using a templating language. JSX is not a templating solution. It is a declarative syntax used to express a tree structure of UI components.
    * The compiler will find errors in your HTML you might otherwise miss.
    * JSX promotes the idea of inline styles. Which can be a good thing.
* Beware of JSX [Gotchas](http://facebook.github.io/react/docs/jsx-gotchas.html).
* A [JSX specification is currently being drafted](https://facebook.github.io/jsx/). It can be used by anyone as an a XML-like syntax extension to ECMAScript without any defined semantics.
