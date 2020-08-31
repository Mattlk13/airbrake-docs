---
layout: classic-docs
title: Performance Monitoring FAQ
short-title: FAQ
categories: [performance-monitoring]
group: About Performance Monitoring
group-position: 3
description: Performance Monitoring FAQ
---

### How can I start collecting performance data for my app?

Just follow the [Performance Monitoring getting started
guide](/docs/performance-monitoring/getting-started/), and you’ll
have real data in your Performance Dashboard in minutes.

### Do I have to install an agent or additional dependency?

No! We’ve bundled Performance Monitoring into our error notifiers. Update your
error notifier to the latest version and you are almost done. The [getting
started guide](/docs/performance-monitoring/getting-started/) can
get you the rest of the way.

### Which Airbrake notifiers are Performance Monitoring compatible?

We currently support Performance Monitoring tracking for
[Rails](/docs/performance-monitoring/getting-started/),
[Node.js (Express.js)](/docs/performance-monitoring/updating-your-node-notifier/),
[Go](/docs/performance-monitoring/go/),
[Django](/docs/performance-monitoring/django/), and
[Flask](/docs/performance-monitoring/flask/) projects.

### How much does Performance Monitoring cost per host?

With Airbrake Performance Monitoring you pay per request, not per host. You can
report performance metrics from as many servers or containers as you like and
only pay for the number of requests that are monitored by Airbrake.

### What does Performance Monitoring cost?

Pricing for Airbrake Performance Monitoring is based on the number of requests
monitored in the monthly billing period. Each month includes a free amount of
usage, making it free and easy to try. You can check the current costs in
[https://airbrake.io/account/edit](https://airbrake.io/account/edit).

### What is a Performance Monitoring request?

A Performance Monitoring request is sent to Airbrake whenever your app serves
an HTTP response; it’s the core unit of data used to provide insight into your
app’s performance. The number of requests monitored are counted against your
monthly Performance Monitoring usage.

### Is Performance Monitoring included in the free trial?

Yes. All new accounts receive a free trial of Airbrake which includes all
Performance Monitoring usage! In addition to this, all accounts receive a free
amount of usage every month.

### Does Airbrake interfere with my other Performance Monitoring tools?

Airbrake Performance Monitoring plays nicely with NewRelic, Skylight, and other
performance monitoring solutions so you can safely try us out when deciding to
switch over from another Performance Monitoring tool.

### How long is performance data retained?

By default we retain performance data for 3 months. If you need a custom data
retention period just email [support@airbrake.io](mailto:support@airbrake.io).

### How is sensitive data handled?

SQL queries and URLs are stripped of sensitive information and normalized
before being reported to Airbrake.

### Where can I find your privacy policy and security information?

Here is our [privacy policy](https://airbrake.io/privacy) and more information
on [security](https://airbrake.io/product/security). Airbrake is SOC 2 Type II,
Privacy Shield, and GDPR compliant.

### When will I be billed for usage?

For a new free trial, you get 30 days of free Performance Monitoring. If you
decide to continue, you will be charged for usage after the free 30 days. If
you are an existing Airbrake user who added Performance Monitoring to your
account your Performance Monitoring usage will be added to your next bill.

### How can I prevent a route from reporting performance?

You can use the `add_performance_filter` method to avoid sending performance
data.You can filter out request data based on any conditions available to your
app. You would place this block below your Airbrake config block in your
airbrake initialization file. This example avoids sending performance data for
requests to an endpoint called `/health_check`:

```ruby
Airbrake.add_performance_filter do |resource|
  resource.ignore! if resource.route =~ %r{/health_check}
end
```

### How are multiple environments handled?

You can send performance data from as many environments as you like. The
environment is selectable option in the Performance Dashboard.

### Have a Performance Monitoring question that’s not on this list?

No problem! Just email [support@airbrake.io](mailto:support@airbrake.io) with
your Performance Monitoring question.
