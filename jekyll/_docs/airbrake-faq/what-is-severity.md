---
layout: classic-docs
title: What is severity?
categories: [airbrake-faq]
description: what severity is and how it is used
---

![severity.png](/docs/assets/img/docs/airbrake/severity.png)

Big Airbrake projects receive a lot of errors. Every new error triggers an email
notification. Not every error is equally important, and a large amount of error
emails can be overwhelming.

### Setting an error's severity

Severity allows you to control the importance of every single error your
notifier sends. Consult your notifier's README to learn how to control severity
for your errors.

Airbrake supports the following severities (defaults to `error`):

* `debug`
* `info`
* `notice`
* `warning`
* `error`
* `critical`
* `alert`
* `emergency`

### Filtering notifications by severity

You can set a minimum severity value in your project settings page. An error
that does not meet the severity threshold will not trigger an email or
integration notifications but will still show up in your project's error
dashboard.

By default, the minimum severity is set to `error`. That means that errors with
a severity of `debug`, `info`, `notice`, or `warning` will not trigger error
emails or integration notifications.

![severity_setting.png](/docs/assets/img/docs/airbrake/severity_setting.png)

Want low severity errors to completely avoid your project? Then you can use
your notifier's **add filter** method to ignore errors based on the severity
value. Please check your notifier's GitHub README for more info and examples.
