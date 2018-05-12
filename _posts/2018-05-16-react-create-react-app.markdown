---
layout: post
title: React - Create React App
date: 2018-05-09
description:
img: create-react-app.png
tags: [react, reactjs, learn react]
---

Setting up Gulp, Webpack, Browserify, Babel, JSX, ES6, ES6 modules, hot reloading, … etc. manually - forget about it and no more fuss with it.


Inspired by the cohesive developer experience provided by Ember.js Facebook wanted to provide an easy way to develop React apps, they created [create-react-app](https://github.com/facebook/create-react-app) with the targets zero configuration.

## Install

You may need [NPM](https://nodejs.org/en/download/) installed and you can use [NVM](https://github.com/creationix/nvm#usage) to easily switch Node versions between different projects.

The Node installation is only required for Create React App itself.

To install create-react-app module:

```javascript
npm install -g create-react-app
```

## Creating an App

To create a new app:

```javascript
create-react-app my-app
```

It will create a directory called geekhmer inside the current folder. And inside that directory, it will generate the initial project structure and install the transitive dependencies:

```javascript
my-app
  README.md
  node_modules/
  package.json
  .gitignore
  public/
    favicon.ico
    index.html
  src/
    App.css
    App.js
    App.test.js
    index.css
    index.js
    logo.svg
```

No configuration or complicated folder structures, just the files you need to build your app.

## Run the App

Runs the app in development mode:

```javascript
npm start
```

Open http://localhost:3000 to view it on the browser.

## Run the Test

Runs the test watcher in an interactive mode:

```javascript
npm test
```

## Builds the App for Production

Builds the app for production to the build folder. It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes. By default, it also includes a service worker so that your app loads from local cache on future visits.

```javascript
npm run build
```

Your app is ready to be deployed. So far so good, I will launch the new one website for learning create-react-app (http://learncreatereactapp.github.io). Stay turn!
