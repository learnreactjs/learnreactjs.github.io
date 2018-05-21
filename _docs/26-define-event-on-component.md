---
title: "Defining Events on Components"
permalink: /define-event-on-component
excerpt: "Defining Events on Components - Learn React"
last_modified_at: 2018-05-19T15:58:49-04:00
---

Events can be added to React nodes inside of a components `render()` method.

In the example, two React events (i.e. `onClick` & `onMouseOver`) are set on React nodes (via JSX) using what looks like component props:

<p data-height="265" data-theme-id="dark" data-slug-hash="XqooOV" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="XqooOV" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/XqooOV/">XqooOV</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

Basically, React when rendering a component looks for special React prop events (e.g. `onClick`) and treats these props differently from other props (all React events shown in table below). The difference being, that eventing in the real DOM is being wired up behind the scenes.

Part of this wiring is auto binding the context of the handler/callback to the scope of the component instance. In the example below the value of `this` inside of the handlers/callbacks will reference the component instance itself.

<p data-height="265" data-theme-id="dark" data-slug-hash="zjyyQW" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="zjyyQW" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/zjyyQW/">zjyyQW</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
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
