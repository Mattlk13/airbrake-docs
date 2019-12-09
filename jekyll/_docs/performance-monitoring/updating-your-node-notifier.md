---
layout: classic-docs
title: Updating your Node.js notifier
short-title: Updating your Node.js notifier
categories: [performance-monitoring]
description: How to update your Node.js notifier for Performance Monitoring
---

Get the most out of Airbrake's features and stay up to date with the latest
improvements by updating your project to the latest version of our Node.js
error reporting library.

## Name change note
Our JavaScript library's name has recently changed from `airbrake-js` to
`@airbrake/node` (for Node.js apps). If you are using `airbrake-js` check out
[our upgrade doc](/docs/performance-monitoring/updating-from-airbrake-js-for-node/).
If you are on the deprecated `node-airbrake` notifier, please
visit [our other upgrade
guide](/docs/performance-monitoring/updating-from-deprecated-libraries-for-node/).

## Update your notifier

If you're using our official notifier, all you need to do is update the version you're using:

```
npm update @airbrake/node
```

Or, if you're using yarn:

```
yarn upgrade @airbrake/node
```

{% include_relative express-install-note.md %}
