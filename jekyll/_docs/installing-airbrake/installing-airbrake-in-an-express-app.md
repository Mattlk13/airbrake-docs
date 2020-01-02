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

{% include_relative airbrake-js/node-installation.md %}

## Configuration

After you have installed the [airbrake-js notifier](https://github.com/airbrake/airbrake-js)
the next step is configuring Airbrake in your Express app.  Configuration
involves creating an `Notifier` with your `projectId` and `projectKey` and
registering an Express error handler. The error handler should be registered
below all other `app.use()` and routes calls.

### Configuring in an example Express app
Here is the configuration for an
[example Express app](https://github.com/airbrake/airbrake-js/tree/master/packages/node/examples/express),
this app throws and reports an error to Airbrake when you visit
 [localhost:3000](http://localhost:3000). You will want to set your
 `AIRBRAKE_PROJECT_ID` and `AIRBRAKE_PROJECT_KEY` with your project's actual ID
 and key (found in your project settings page).

```js
const express = require('express');
const pg = require('pg');

const Airbrake = require('@airbrake/node');
const airbrakeExpress = require('@airbrake/node/dist/instrumentation/express');
const airbrakePG = require('@airbrake/node/dist/instrumentation/pg');

async function main() {
  const airbrake = new Airbrake.Notifier({
    projectId: process.env.AIRBRAKE_PROJECT_ID,
    projectKey: process.env.AIRBRAKE_PROJECT_KEY,
  });

  console.log(pg.Client.prototype.query);

  const client = new pg.Client();
  await client.connect();

  const app = express();

  // This middleware should be added before any routes are defined.
  app.use(airbrakeExpress.makeMiddleware(airbrake));

  app.get('/', async function home(req, res) {
    const result = await client.query('SELECT $1::text as message', [
      'Hello world!',
    ]);
    console.log(result.rows[0].message);

    res.send('Hello World!');
  });

  app.get('/hello/:name', function hello(req, res) {
    throw new Error('hello from Express');
    res.send(`Hello ${req.params.name}`);
  });

  // Error handler middleware should be the last one.
  // See http://expressjs.com/en/guide/error-handling.html
  app.use(airbrakeExpress.makeErrorHandler(airbrake));

  app.listen(3000, function() {
    console.log('Example app listening on port 3000!');
  });
}

main();
```

{% include_relative airbrake-js/going-further.md %}
