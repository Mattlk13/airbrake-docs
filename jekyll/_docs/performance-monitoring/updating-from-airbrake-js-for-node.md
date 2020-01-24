---
layout: classic-docs
title: Updating from airbrake-js for Node.js projects
short-title: Updating from airbrake-js for Node.js projects
categories: [performance-monitoring]
description: How to update your Node.js project's notifier from airbrake-js
---

Get the most out of Airbrake's features and stay up to date with the latest
improvements by updating your project to the latest version of our Node.js
error reporting library.

## Name change note
Our JavaScript library's name has recently changed from `airbrake-js` to
`@airbrake/node` (for Node.js apps). If you are using `airbrake-js`, we would
recommend following this guide to update to the latest version of our
JavaScript library.

## Step 1: Uninstall `airbrake-js`

Uninstall the old package:

```shell
npm uninstall airbrake-js
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

#### Imports: Replace old library import:
```js
var AirbrakeClient = require('airbrake-js');
```

With new package name:

```js
var Airbrake = require('@airbrake/node');
```

#### Class names:

Replace configuration snippet instantiation with new name:

Change `AirbrakeClient()` to new name: `Airbrake.Notifier()` in your
configuration snippet:

```js
var airbrake = new Airbrake.Notifier({
  // project credentials are set here...
});
```

Find advanced configuration options and examples on our [official GitHub
repo](https://github.com/airbrake/airbrake-js/tree/master/packages/node).

{% include_relative express-install-note.md %}
