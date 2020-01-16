---
layout: classic-docs
title: Installing Airbrake in an Express application
short-title: Express
language: express
categories: [installing-airbrake]
description: Installing Airbrake in an Express application
---

![](https://s3.amazonaws.com/document-resources/jsbrakeman.png)

{% include_relative airbrake-js/features.md %}

# Using Airbrake with Express.js

This example Node.js application uses Express.js and sets up Airbrake to report
errors and performance data. To adapt this example to your app, follow these
steps:

#### 1. Install the package
```shell
npm install @airbrake/node
```

We also support installation via
[yarn](https://github.com/airbrake/airbrake-js/tree/master/packages/node#installation).


#### 2. Include airbrake-js in your app
Include the required airbrake-js libraries in your `app.js`

```js
const Airbrake = require('@airbrake/node');
const airbrakeExpress = require('@airbrake/node/dist/instrumentation/express');
const airbrakePG = require('@airbrake/node/dist/instrumentation/pg');
```

#### 3. Configure Airbrake with your project's credentials

```js
const airbrake = new Airbrake.Notifier({
  projectId: process.env.AIRBRAKE_PROJECT_ID,
  projectKey: process.env.AIRBRAKE_PROJECT_KEY,
});
```

#### 4. Add the Airbrake Express middleware
This middleware should be added before any routes are defined.

```js
app.use(airbrakeExpress.makeMiddleware(airbrake));
```

#### 5. Add the Airbrake Express error handler
The error handler middleware should be defined last. For more info on how this
works, see the official
[Express error handling doc](http://expressjs.com/en/guide/error-handling.html).

```js
app.use(airbrakeExpress.makeErrorHandler(airbrake));
```

#### 6. Run your app
The last step is to run your app. To test that you've configured Airbrake
correctly, you can throw an error inside any of your routes:
```js
app.get('/hello/:name', function hello(req, res) {
  throw new Error('hello from Express');
  res.send(`Hello ${req.params.name}`);
});
```


Any unhandled errors that are thrown will now be reported to Airbrake. See the
[basic usage](https://github.com/airbrake/airbrake-js/tree/master/packages/node#basic-usage)
to learn how to manually send errors to Airbrake and other advanced options.

To see this all in action, check out
[the full `app.js` file](https://github.com/airbrake/airbrake-js/blob/master/packages/node/examples/express/app.js)
in our
[example](https://github.com/airbrake/airbrake-js/blob/master/packages/node/examples/express)
on GitHub.
