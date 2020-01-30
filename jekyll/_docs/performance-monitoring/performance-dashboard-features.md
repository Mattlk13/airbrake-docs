---
layout: classic-docs
title: Performance Dashboard Features
short-title: Dashboard Features
categories: [performance-monitoring]
group: About Performance Monitoring
group-position: 2
description: Performance Dashboard Features
---

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
