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
  - [Angular](/docs/installing-airbrake/installing-airbrake-in-an-angular-app/)
  - [Express](/docs/installing-airbrake/installing-airbrake-in-an-express-app/)
  - [Legacy](https://github.com/airbrake/airbrake-js/tree/master/examples/legacy)
  - [Node.js](/docs/installing-airbrake/installing-airbrake-in-a-node-app/)
  - [Rails](/docs/installing-airbrake/installing-airbrake-js-in-a-rails-app/)
  - [React](/docs/installing-airbrake/installing-airbrake-in-a-react-app/)
  - [Redux](/docs/installing-airbrake/installing-airbrake-in-a-redux-app/)
  - [Vue.js](/docs/installing-airbrake/installing-airbrake-in-a-vuejs-app/)

{% include_relative airbrake-js/installation.md %}

## Setup

Starting from v2 @airbrake/browser uses [rollup.js](https://rollupjs.org) to provide 3 separate build formats:

- dist/airbrake.iife.js - a self-executing function, suitable for inclusion as a <script> tag.
- dist/airbrake.esm.js - an ES module file, suitable for other bundlers and inclusion as a <script type=module> tag in modern browsers.
- dist/airbrake.common.js - CommonJS, suitable for Node.js and other bundlers.

Your package manager should automatically pick suitable bundle format based on @airbrake/browser package.json file:

```js
  "main": "dist/airbrake.common.js",
  "web": "dist/airbrake.iife.js",
  "module": "dist/airbrake.esm.js",
  "jsnext:main": "dist/airbrake.esm.js",
  "types": "dist/airbrake.d.ts",
  "source": "src/index.ts",
```

## Basic Usage

First you need to initialize the notifier with the project id and API key taken from [Airbrake.io](https://airbrake.io):

```js
import { Notifier } from '@airbrake/browser';

const airbrake = new Notifier({
  projectId: 1,
  projectKey: 'REPLACE_ME',
  environment: 'production',
});
```

Then you can send a textual message to Airbrake:

```js
let promise = airbrake.notify(`user id=${user_id} not found`);
promise.then(function(notice) {
  if (notice.id) {
    console.log('notice id', notice.id);
  } else {
    console.log('notify failed', notice.error);
  }
});
```

Or report caught errors directly:

```js
try {
  // This will throw if the document has no head tag
  document.head.insertBefore(document.createElement('style'));
} catch(err) {
  airbrake.notify(err);
  throw err;
}
```

Alternatively, you can wrap any code which may throw errors using the client's `wrap` method:

```js
let startApp = function() {
  // This will throw if the document has no head tag.
  document.head.insertBefore(document.createElement('style'));
}
startApp = airbrake.wrap(startApp);

// Any exceptions thrown in startApp will be reported to Airbrake.
startApp();
```

{% include_relative airbrake-js/going-further.md %}
