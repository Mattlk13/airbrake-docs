---
layout: classic-docs
title: Breadcrumbs for JavaScript
short-title: Breadcrumbs
categories: [features]
description: Breadcrumbs for JavaScript projects
---

## What are Breadcrumbs?
Breadcrumbs are a snapshot of events that lead up to a specific error
occurrence. Things like web requests, user interactions like clicks or keyboard
presses, and navigation updates are all recorded and organized in a timeline so
you can understand what actually happened when an error occurred.

Breadcrumbs are available on [all paid plans](https://airbrake.io/pricing).

### Events that are logged as Breadcrumbs

* Log events with severity
* User events like clicks and keypresses
* XMLHttpRequests like POST and GET events
* DOMContentLoaded events
* Errors in loading page elements or scripts
* Navigation from page to page
* Window fully loaded events

## Breadcrumbs UI
Breadcrumb data is displayed in the "Occurrences" tab of an error.

![breadcrumbs](/docs/assets/img/docs/installing_airbrake/breadcrumbs.png)

## Logging Breadcrumbs
Breadcrumbs are logged automatically if you're using version `0.7.0` and higher
of our [JavaScript notifier](https://github.com/airbrake/airbrake-js).

## Disabling Breadcrumbs
Don't want airbrake-js to send Breadcrumb data to Airbrake? No problem, you can
strip errors of Breadcrumb data using the
[`addFilter` method](https://github.com/airbrake/airbrake-js/tree/master/packages/browser#filtering-errors):

```js
airbrake.addFilter(function(notice) {
  notice.context.history = null;
  return notice;
});
```

