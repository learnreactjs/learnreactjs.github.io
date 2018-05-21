---
title: "Using ES with React"
permalink: /use-es-with-react
excerpt: "Using ES with React - Learn React"
last_modified_at: 2018-05-16T15:58:49-04:00
---

Babel is not part of React. In fact, Babel's purpose isn't even that of a JSX transformer. Babel is a JavaScript compiler. It takes ES* code and transforms it to run in browsers that don't support ES* code. As of today, Babel mostly takes ES6 and ES7 code and transforms it into ES5 code. When doing these ECMAScript transformations it is trivial to also transform JSX expressions into `React.createElement()` calls. This is what we examined in the previous section.

In the HTML page below the familiar `HelloMessage` component has been rewritten to [take advantage](http://babeljs.io/blog/2015/06/07/react-on-es6-plus) of [ES6 classes](https://github.com/lukehoban/es6features#classes). Not only is Babel transforming the JSX syntax, it is also transforming ES6 class syntax to ES5 syntax which can then be parsed by ES5 browser engines.

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
      class HelloMessage extends React.Component {
        render(){
          return <div>Hello {this.props.name}</div>;
        }
      };

      ReactDOM.render(
        <HelloMessage name="Brian" />, 
        document.getElementById('app')
      );

      /*** PREVIOUSLY ***/
      /*  var HelloMessage = createReactClass({
       *    render: function() {
       *      return <div>Hello {this.props.name}</div>;
       *    }
       *  });
       *
       *  ReactDOM.render(
       *    <HelloMessage name="Brian" />, 
       *    document.getElementById('app')
       *  );
       ******************/
      </script>
  </body>
</html>
```

In the above HTML document Babel is taking in:

```
class HelloMessage extends React.Component {
  render(){
    return <div>Hello {this.props.name}</div>;
  }
};

ReactDOM.render(
  <HelloMessage name="Brian" />, 
  document.getElementById('app')
);
```

Transforming it to this:

```
"use strict";

var _createClass = (function () { function defineProperties(target, props) { for (var i = 0; i < props.length; i++) { var descriptor = props[i]; descriptor.enumerable = descriptor.enumerable || false; descriptor.configurable = true; if ("value" in descriptor) descriptor.writable = true; Object.defineProperty(target, descriptor.key, descriptor); } } return function (Constructor, protoProps, staticProps) { if (protoProps) defineProperties(Constructor.prototype, protoProps); if (staticProps) defineProperties(Constructor, staticProps); return Constructor; }; })();

var _get = function get(_x, _x2, _x3) { var _again = true; _function: while (_again) { var object = _x, property = _x2, receiver = _x3; _again = false; if (object === null) object = Function.prototype; var desc = Object.getOwnPropertyDescriptor(object, property); if (desc === undefined) { var parent = Object.getPrototypeOf(object); if (parent === null) { return undefined; } else { _x = parent; _x2 = property; _x3 = receiver; _again = true; desc = parent = undefined; continue _function; } } else if ("value" in desc) { return desc.value; } else { var getter = desc.get; if (getter === undefined) { return undefined; } return getter.call(receiver); } } };

function _classCallCheck(instance, Constructor) { if (!(instance instanceof Constructor)) { throw new TypeError("Cannot call a class as a function"); } }

function _inherits(subClass, superClass) { if (typeof superClass !== "function" && superClass !== null) { throw new TypeError("Super expression must either be null or a function, not " + typeof superClass); } subClass.prototype = Object.create(superClass && superClass.prototype, { constructor: { value: subClass, enumerable: false, writable: true, configurable: true } }); if (superClass) Object.setPrototypeOf ? Object.setPrototypeOf(subClass, superClass) : subClass.__proto__ = superClass; }

var HelloMessage = (function (_React$Component) {
  _inherits(HelloMessage, _React$Component);

  function HelloMessage() {
    _classCallCheck(this, HelloMessage);

    _get(Object.getPrototypeOf(HelloMessage.prototype), "constructor", this).apply(this, arguments);
  }

  _createClass(HelloMessage, [{
    key: "render",
    value: function render() {
      return React.createElement(
        "div",
        null,
        "Hello ",
        this.props.name
      );
    }
  }]);

  return HelloMessage;
})(React.Component);

;

ReactDOM.render(React.createElement(HelloMessage, { name: "Brian" }), document.getElementById('app'));
```

Most [ES6 features](https://github.com/lukehoban/es6features) with a few caveats can be used when writing JavaScript that is transformed by Babel.
