---
layout: classic-docs
title: Installing Airbrake in a JavaScript application
short-title: JavaScript
language: javascript
categories: [installing-airbrake]
description: Installing Airbrake in a Javascript application
---

![](https://s3.amazonaws.com/document-resources/jsbrakeman.png)

{% include_relative airbrake-js/features.md %}

## Supported frameworks
  - [AngularJS](/docs/installing-airbrake/installing-airbrake-in-an-angularjs-app/)
  - [Angular 2 and above](/docs/installing-airbrake/installing-airbrake-in-an-angular-2-app/)
  - [Browserify](/docs/installing-airbrake/installing-airbrake-in-a-browserify-app/)
  - [Express](/docs/installing-airbrake/installing-airbrake-in-an-express-app/)
  - [Legacy](https://github.com/airbrake/airbrake-js/tree/master/examples/legacy)
  - [Node.js](/docs/installing-airbrake/installing-airbrake-in-a-node-app/)
  - [Rails](/docs/installing-airbrake/installing-airbrake-js-in-a-rails-app/)
  - [React](/docs/installing-airbrake/installing-airbrake-in-a-react-app/)
  - [Redux](/docs/installing-airbrake/installing-airbrake-in-a-redux-app/)
  - [Vue.js](/docs/installing-airbrake/installing-airbrake-in-a-vuejs-app/)

{% include_relative airbrake-js/installation.md %}

## Basic Usage

First you need to initialize notifier with project id and API key taken from [Airbrake.io](https://airbrake.io):

```js
var airbrake = new airbrakeJs.Client({projectId: 1, projectKey: 'abc'});
```

Or if you are using browserify/webpack/etc:

```js
var airbrakeJs = require('airbrake-js');
var airbrake = new airbrakeJs({projectId: 1, projectKey: 'abc'});
```

The simplest method is to report errors directly:

```js
try {
  // This will throw if the document has no head tag
  document.head.insertBefore(document.createElement("style"));
} catch(err) {
  airbrake.notify(err);
  throw err;
}
```

Alternatively you can wrap any code which may throw errors using the client's `wrap` method:

```js
var startApp = function() {
  // This will throw if the document has no head tag.
  document.head.insertBefore(document.createElement("style"));
}
startApp = airbrake.wrap(startApp);

// Any exceptions thrown in startApp will be reported to Airbrake.
startApp();
```

{% include_relative airbrake-js/going-further.md %}
