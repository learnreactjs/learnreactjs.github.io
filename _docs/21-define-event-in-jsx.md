---
title: "Defining Events in JSX"
permalink: /define-event-in-jsx
excerpt: "Defining Events in JSX - Learn React"
last_modified_at: 2018-05-19T15:58:49-04:00
---

In the [previous chapter](/define-react-node-event), it was explained how events are defined on React nodes. To do the same thing in JSX you add the same camelCased event and the corresponding handler/callback as a prop/attribute of the JSX representing the React node.

Below is the none JSX way of adding an event to a React node:

<p data-height="265" data-theme-id="dark" data-slug-hash="PedNxy" data-default-tab="result" data-user="Bunlong" data-embed-version="2" data-pen-title="PedNxy" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/PedNxy/">PedNxy</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

The above code written using JSX:

<p data-height="265" data-theme-id="dark" data-slug-hash="wjRyQr" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="wjRyQr" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/wjRyQr/">wjRyQr</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

Note that we are using the `{ }` brackets to connect a JS function to an event (i.e. `onMouseOver={mouseOverHandler}`).

The table below outlines the unique SyntheticEvent properties for each type/category of events.

| Type/Category | Events           | Properties       |
|:--------------|:-----------------|:-----------------|
| Clipboard     | onCopy, onCut, onPaste | DOMDataTransfer, clipboardData |
| Composition   | onCompositionEnd, onCompositionStart, onCompositionUpdate | data |
| Keyboard      | onKeyDown, onKeyPress, onKeyUp | altKey, charCode, ctrlKey, getModifierState(key), key, keyCode, locale, location, metaKey, repeat, shiftKey, which |
| Focus         | onChange, onInput, onSubmit | DOMEventTarget, relatedTarget |
| Form          | onFocus, onBlur |                   |
| Mouse         | onClick, onContextMenu, onDoubleClick, onDrag, onDragEnd, onDragEnter, onDragExit onDragLeave, onDragOver, onDragStart, onDrop, onMouseDown, onMouseEnter, onMouseLeave onMouseMove, onMouseOut, onMouseOver, onMouseUp | altKey, button, buttons, clientX, clientY, ctrlKey, getModifierState(key), metaKey, pageX, pageY, DOMEventTarget relatedTarget, screenX, screenY, shiftKey |
| Selection     | onSelect         | |
| Touch         | onTouchCancel, onTouchEnd, onTouchMove, onTouchStart | altKey DOMTouchList changedTouches, ctrlKey, getModifierState(key), metaKey, shiftKey, DOMTouchList targetTouches, DOMTouchList touches |
| UI            | onScroll         | detail, DOMAbstractView view |
| Wheel         | onWheel          | deltaMode, deltaX, deltaY, deltaZ |
| Media         | onAbort, onCanPlay, onCanPlayThrough, onDurationChange, onEmptied, onEncrypted, onEnded, onError, onLoadedData, onLoadedMetadata, onLoadStart, onPause, onPlay, onPlaying, onProgress, onRateChange, onSeeked, onSeeking, onStalled, onSuspend, onTimeUpdate, onVolumeChange, onWaiting | |
| Image         | onLoad, onError  | |
| Animation     | onAnimationStart, onAnimationEnd, onAnimationIteration | animationName, pseudoElement, elapsedTime |
| Transition    | onTransitionEnd  | propertyName, pseudoElement, elapsedTime |

Note: 

* Not all DOM events are provided by React. But you can still make use of them [using React lifecycle methods](https://reactjs.org/docs/react-component.html).