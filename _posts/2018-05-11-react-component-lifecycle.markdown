---
layout: post
title: React - Component Lifecycle
date: 2018-05-07
description: 
img: react-component-lifecycle.png
tags: [react, reactjs, learn react]
---

ReactJS components have three main parts of their lifecycle:

* ***Mounting:*** A component is being inserted into the DOM.

* ***Updating:*** A component is being re-rendered to determine if the DOM should be updated.

* ***Unmounting:*** A component is being removed from the DOM.

React provides lifecycle methods that you can specify to hook into this process. 

We provide `will` methods, which are called right before something happens, and `did` methods which are called right after something happens.

