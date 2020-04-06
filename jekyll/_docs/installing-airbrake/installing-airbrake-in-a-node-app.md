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
const http = require('http');
const Airbrake = require('@airbrake/node');

new Airbrake.Notifier({
  projectId: process.env.AIRBRAKE_PROJECT_ID,
  projectKey: process.env.AIRBRAKE_PROJECT_KEY,
});

const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((_req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World');
  throw new Error('I am an uncaught exception');
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```

*For our [full Node example app code](https://github.com/airbrake/airbrake-js/tree/master/packages/node/examples) and more information, please visit our [official GitHub repo](https://github.com/airbrake/airbrake-js/tree/master/packages/node).*
