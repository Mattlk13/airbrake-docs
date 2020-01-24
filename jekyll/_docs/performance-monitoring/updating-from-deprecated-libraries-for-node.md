---
layout: classic-docs
title: Updating from node-airbrake for Node.js projects
short-title: Updating from node-airbrake for Node.js projects
categories: [performance-monitoring]
description: How to update your Node.js project's notifier from node-airbrake
---

Get the most out of Airbrake's features and stay up to date with the latest
improvements by updating your project to the latest version of our Node.js
error reporting library.

## Library note
This update guide is for projects on
[`node-airbrake`](https://github.com/airbrake/node-airbrake). For projects on
`airbrake-js`, please visit [our other
guide](/docs/performance-monitoring/updating-from-airbrake-js-for-node/). For
projects on [`@airbrake/node`](https://github.com/airbrake/node-airbrake),
please visit [our other
guide](/docs/performance-monitoring/updating-your-node-notifier/).

## Step 1: Uninstall `airbrake`

Uninstall the old package:

```shell
npm uninstall airbrake
```

## Step 2: Install `@airbrake/node`

Install the new package with NPM:

```shell
npm install @airbrake/node
```

We also support installation via
[Yarn](https://github.com/airbrake/airbrake-js/tree/master/packages/node#installation).

## Step 3: Replace mentions with new library

_**Note:** Express.js users should follow our **[Express.js install
guide](/docs/installing-airbrake/installing-airbrake-in-an-express-app/)**._

Replace old configuration snippet instantiation:

```js
var airbrake = require('airbrake').createClient(
  '123987',       // Project ID
  'abcdefg123456' // Project key
);
airbrake.handleExceptions();
```

With new package format:

```js
var Airbrake = require('@airbrake/node');

var airbrake = new Airbrake.Notifier({
  projectId: '123987',
  projectKey: 'abcdefg123456',
});
```

Find advanced configuration options and examples on our [official GitHub
repo](https://github.com/airbrake/airbrake-js/tree/master/packages/node).

{% include_relative express-install-note.md %}
