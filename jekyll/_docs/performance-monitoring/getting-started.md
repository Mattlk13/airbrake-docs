---
layout: classic-docs
title: Performance Monitoring Getting Started
short-title: Performance Monitoring Getting Started
categories: [performance-monitoring]
description: Getting Started with Performance Monitoring
---

{% include_relative performance-monitoring-features.md %}

## Supported languages
- Rails (instructions below)
- [Node.js (Express.js) setup guide](/docs/performance-monitoring/updating-your-node-notifier/)
- [Go setup guide](/docs/performance-monitoring/go/)
- [Django setup guide](/docs/performance-monitoring/django/)
- [Flask documentation](/docs/performance-monitoring/flask/)

## Rails installation

Performance Monitoring is built into the same notifier you use to report errors
from your application. To start sending performance data for your app to
Airbrake just install or upgrade the Airbrake gem to the latest version.

### Step 1: Install the latest version of the Airbrake gem

Add the Airbrake gem to your `Gemfile`:

```ruby
gem 'airbrake'
```

To integrate Airbrake with your Rails application, invoke the following command
and replace `PROJECT_ID` and `PROJECT_KEY` with your project's values:

```shell
rails g airbrake PROJECT_ID PROJECT_KEY
```
After you deploy this Airbrake upgrade you will start seeing your applications
performance stats in the dashboard.

If you run into any issues, we are happy to help. Just let us know
what happened at [support@airbrake.io](mailto:support@airbrake.io).

### Upgrading from a previous gem version?

If you are upgrading from a previous version of our gem, please follow [our
upgrade guide](/docs/ruby/upgrading-your-notifier/) to get started with
Performance Monitoring.

## Performance Dashboard Features

View all of your app’s performance stats at a glance. Trend cards highlight key
performance metrics across your whole app. The charts show requests, response
times, errors, and user satisfaction ([Apdex](https://apdex.org/apdexfaq.html))
over time. The routes list exposes performance stats per route, making it easy
to pinpoint and resolve issues.

![Performance Dashboard](/docs/assets/img/docs/performance_monitoring/performance-dashboard.png)

### Detailed route performance

Diving deeper into an individual route, you can see the proportion of time
spent in the database, cache, views, or making external requests. There are
similar trend cards and performance charts to quickly understand the route
performance. You can also click through from a route to its linked Airbrake
errors.

![Route View](/docs/assets/img/docs/performance_monitoring/route-view.png)

Have questions about Performance Monitoring? Check out our [Performance
Monitoring FAQ](/docs/performance-monitoring/frequently-asked-questions/) for
more information.
