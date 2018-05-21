---
title: "Defining React Node Events"
permalink: /define-react-node-event
excerpt: "Defining React Node Events - Learn React"
last_modified_at: 2018-05-16T15:58:49-04:00
---

Events can be added to React nodes like events can be added to DOM nodes. In the example below I am adding a very simple click and mouseover event to a React `<div>` node.

<p data-height="265" data-theme-id="dark" data-slug-hash="PedNxy" data-default-tab="result" data-user="Bunlong" data-embed-version="2" data-pen-title="PedNxy" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/PedNxy/">PedNxy</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

Note how the property name for an event in React starts with 'on' and is passed in the props argument object to the `ReactElement()` function.

React creates what it calls a [SyntheticEvent](https://reactjs.org/docs/events.html) for each event, which contains the details for the event. Similar to the details that are defined for DOM events. The `SyntheticEvent` instance, for an event, is passed into the events handlers/callback functions. In the code below I am logging the details of a SyntheticEvent instance.

<p data-height="265" data-theme-id="dark" data-slug-hash="zjyqpb" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="zjyqpb" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/zjyqpb/">zjyqpb</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

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