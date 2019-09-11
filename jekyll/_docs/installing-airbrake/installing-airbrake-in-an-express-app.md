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

{% include_relative airbrake-js/installation.md %}

## Configuration

After you have installed the [airbrake-js notifier](https://github.com/airbrake/airbrake-js)
the next step is configuring Airbrake in your Express app.  Configuration
involves creating an `AirbrakeClient` with your `projectId` and `projectKey` and
registering an Express error handler. The error handler should be registered
below all other `app.use()` and routes calls.

### Configuring in an example Express app
Here is the configuration for an
[example Express app](https://github.com/airbrake/airbrake-js/tree/master/packages/node/examples/express),
this app throws and reports an error to Airbrake when you visit
 [localhost:3000](http://localhost:3000). You will want to replace the
placeholder `projectId` and `projectKey` with the real values from your
project's settings page.

```js
var express = require('express');
var AirbrakeClient = require('airbrake-js');
var makeErrorHandler = require('airbrake-js/dist/instrumentation/express');

var app = express();

app.get('/', function hello (req, res) {
  throw new Error('hello from Express');
  res.send('Hello World!');
})

var airbrake = new AirbrakeClient({
  projectId: 1,
  projectKey: 'FIXME',
});

// Error handler middleware should be the last, after other app.use() and routes calls.
// http://expressjs.com/en/guide/error-handling.html
app.use(makeErrorHandler(airbrake));

app.listen(3000, function () {
  console.log('Example app listening on port 3000!');
})
```

{% include_relative airbrake-js/going-further.md %}
