---
layout: classic-docs
title: Installing Airbrake in a Browserify application
short-title: Browserify
language: browserify
categories: [installing-airbrake]
description: Installing Airbrake in a Browserify application
---

![](https://s3.amazonaws.com/document-resources/jsbrakeman.png)

{% include_relative airbrake-js/features.md %}

{% include_relative airbrake-js/installation.md %}

## Configuration

To report errors from your Browserify app you configure an `AirbrakeClient` with
your `projectId` and `projectKey` and report errors with the `notify` function.
Here is an example from our
[Browserify example app](https://github.com/airbrake/airbrake-js/tree/master/packages/browser/examples/browserify):

```js
{% include_relative airbrake-js/browserify/app.js %}
```

{% include_relative airbrake-js/going-further.md %}
