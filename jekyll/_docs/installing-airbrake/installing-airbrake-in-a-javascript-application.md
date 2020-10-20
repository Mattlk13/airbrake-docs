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
  - [Legacy](https://github.com/airbrake/airbrake-js/blob/master/packages/browser/examples/legacy)
  - [Node.js](/docs/installing-airbrake/installing-airbrake-in-a-node-app/)
  - [Rails](/docs/installing-airbrake/installing-airbrake-js-in-a-rails-app/)
  - [React](/docs/installing-airbrake/installing-airbrake-in-a-react-app/)
  - [Redux](/docs/installing-airbrake/installing-airbrake-in-a-redux-app/)
  - [Vue.js](/docs/installing-airbrake/installing-airbrake-in-a-vuejs-app/)

{% include_relative airbrake-js/installation.md %}

## Basic Usage

First, initialize the notifier with the project ID and API key taken from
[Airbrake](https://airbrake.io):

```js
import { Notifier } from '@airbrake/browser';

const airbrake = new Notifier({
  projectId: 1,
  projectKey: 'REPLACE_ME',
  environment: 'production',
});
```

Then, you can send a textual message to Airbrake:

```js
let promise = airbrake.notify(`user id=${user_id} not found`);
promise.then((notice) => {
  if (notice.id) {
    console.log('notice id', notice.id);
  } else {
    console.log('notify failed', notice.error);
  }
});
```

or report errors directly:

```js
try {
  new Error('Hello from Airbrake!');
} catch(err) {
  airbrake.notify(err);
  throw err;
}
```

Alternatively, you can wrap any code which may throw errors using the `wrap`
method:

```js
let startApp = () => {
  new Error('Hello from Airbrake!');
};
startApp = airbrake.wrap(startApp);

// Any exceptions thrown in startApp will be reported to Airbrake.
startApp();
```

or use the `call` shortcut:

```js
let startApp = () => {
  new Error('Hello from Airbrake!');
};

airbrake.call(startApp);
```

{% include_relative airbrake-js/going-further.md %}
