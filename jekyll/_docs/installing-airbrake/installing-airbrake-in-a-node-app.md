---
layout: classic-docs
title: Installing Airbrake in a Node.js app
short-title: Node.js
language: nodejs
categories: [installing-airbrake]
description: installing airbrake in a node app
---
![node flag](/docs/assets/img/docs/node_flag.jpeg)

{% include_relative airbrake-js/features.md %}

{% include_relative airbrake-js/node-installation.md %}

## Configuration

This is a simple Node app `app.js` file that throws an error and sends it to Airbrake. To configure Airbrake in your project, just `require` the `@airbrake/node` library and instantiate the notifier as shown:

```js
var http = require('http');
var Airbrake = require('@airbrake/node');

http
  .createServer(function(req, res) {
    if (req.url === '/favicon.ico') {
      res.writeHead(404);
      res.end();
      return;
    }

    res.writeHead(200, { 'Content-Type': 'text/plain' });
    res.end('Hello World\n');
    throw new Error('I am an uncaught exception');
  })
  .listen(8080);

console.log('Server running on port 8080.');

var airbrake = new Airbrake.Notifier({
  projectId: process.env.AIRBRAKE_PROJECT_ID,
  projectKey: process.env.AIRBRAKE_PROJECT_KEY,
});
```

*For our [full Node example app code](https://github.com/airbrake/airbrake-js/tree/master/packages/node/examples) and more information, please visit our [official GitHub repo](https://github.com/airbrake/airbrake-js/tree/master/packages/node).*
