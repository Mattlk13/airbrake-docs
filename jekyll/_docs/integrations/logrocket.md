---
layout: classic-docs
title: Integrate LogRocket with Airbrake
short-title: LogRocket
categories: [integrations]
description: Integrate LogRocket with Airbrake
---

Use [LogRocket](https://logrocket.com/) in your JavaScript application?
Integrating Airbrake with LogRocket allows you to view the specific LogRocket
session for the errors in your Airbrake project.

All of this can be done by using your Airbrake notifier's `addFilter`
method.

Copy and paste this snippet into your JavaScript Airbrake config:

```js
airbrake.addFilter(function(notice) {
  notice.context.sessionURL = LogRocket.sessionURL;
  return notice;
});
```
[More info on using `addFilter`](https://github.com/airbrake/airbrake-js/tree/master/packages/browser#filtering-errors)
