---
title: "What Is JSX?"
permalink: /what-is-jsx
excerpt: "What Is JSX? - Learn React"
last_modified_at: 2018-05-18T15:58:49-04:00
---

JSX is an XML/HTML-like syntax used by React that extends ECMAScript so that XML/HTML-like text can co-exist with JavaScript/React code. The syntax is intended to be used by preprocessors (i.e., transpilers like Babel) to transform HTML-like text found in JavaScript files into standard JavaScript objects that a JavaScript engine will parse.

Basically, by using JSX you can write concise HTML/XML-like structures (e.g., DOM like tree structures) in the same file as you write JavaScript code, then Babel will transform these expressions into actual JavaScript code. Unlike the past, instead of putting JavaScript into HTML, JSX allows us to put HTML into JavaScript.

By using JSX one can write the following JSX/JavaScript code:

```javascript
var nav = (
  <ul id="nav">
    <li><a href="#">Home</a></li>
    <li><a href="#">About</a></li>
    <li><a href="#">Clients</a></li>
    <li><a href="#">Contact Us</a></li>
  </ul>
);
```

And Babel will transform it into this:

```javascript
var nav = React.createElement(
  "ul",
  { id: "nav" },
  React.createElement(
    "li",
    null,
    React.createElement(
      "a",
      { href: "#" },
      "Home"
    )
  ),
  React.createElement(
    "li",
    null,
    React.createElement(
      "a",
      { href: "#" },
      "About"
    )
 ),
  React.createElement(
    "li",
    null,
    React.createElement(
      "a",
      { href: "#" },
      "Clients"
    )
  ),
  React.createElement(
    "li",
    null,
    React.createElement(
      "a",
      { href: "#" },
      "Contact Us"
    )
  )
);
```

You can think of JSX as a shorthand for `calling React.createElement()`.

The idea of mixing HTML and JavaScript in the same file can be a rather contentious topic. Ignore the debate. Use it if you find it helpful. If not, write the React code required to create React nodes. Your choice.

In my opinion is that JSX provides a concise and familiar syntax for defining a tree structure with attributes that does not require learning a templating language or leaving JavaScript. Both of which can be a win when building large applications.

JSX is easier to read and write over large pyramids of JavaScript function calls or object literals. 

Additionally the React team clearly believes JSX is better suited for defining UI's than a traditional templating.

Note:

* JSX is simply converting XML-like markup into JavaScript.
* JSX bullet points:
  * Less technical people can still understand and modify the required parts. CSS developers and designers will find JSX more familiar than JavaScript alone.
  * You can leverage the full power of JavaScript in HTML and avoid learning or using a templating language. JSX is not a templating solution. It is a declarative syntax used to express a tree structure of UI nodes and components.
  * By adding a JSX transformation step you'll find errors in your HTML you might otherwise miss.
  * JSX promotes the idea of inline styles. Which can be a good thing.
* JSX is a separate thing from React itself. JSX is designed as an ECMAScript feature and the similarity to XML/HTML is only at the surface.
* In JSX, `<foo-bar />` alone is valid while `<foo-bar>` alone isn't. You have to close all tags, always.
