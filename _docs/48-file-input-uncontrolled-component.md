---
title: "File Input"
permalink: /file-input-uncontrolled-component
excerpt: "File Input Uncontrolled Component - Learn React"
last_modified_at: 2018-05-23T15:58:49-04:00
---

In HTML, an `<input type="file">` lets the user choose one or more files from their device storage to be uploaded to a server or manipulated by JavaScript via the [File API](https://developer.mozilla.org/en-US/docs/Web/API/File/Using_files_from_web_applications).

In React, an `<input type="file">` is always an uncontrolled component because its value can only be set by a user, and not programmatically.

You should use the [File API](https://developer.mozilla.org/en-US/docs/Web/API/File/Using_files_from_web_applications) to interact with the files. 

The example below I shows how to create a `ref` to the DOM node to access file(s) in a submit handler:

<p data-height="265" data-theme-id="0" data-slug-hash="JvqMpG" data-default-tab="js,result" data-user="Bunlong" data-embed-version="2" data-pen-title="JvqMpG" class="codepen">See the Pen <a href="https://codepen.io/Bunlong/pen/JvqMpG/">JvqMpG</a> by Bunlong (<a href="https://codepen.io/Bunlong">@Bunlong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>
