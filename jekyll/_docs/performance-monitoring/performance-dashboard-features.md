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

### Background job monitoring

Automatically track background job performance for all your apps. Measure and
improve the quality of your background jobs and easily gain insight into job
failure rates and duration issues. You can find your app's job performance from
the jobs tab of the performance dashboard.

![Jobs View](/docs/assets/img/docs/performance_monitoring/background-jobs.png)

#### Supported Background Job libraries
- **Ruby** supports automatic job tracking for
   - Sidekiq, Resque, Sneakers, DelayedJob, ActiveJob, and Shoryuken
- **Python** supports automatic job tracking for Celery [with minimal setup](https://github.com/airbrake/pybrake/blob/master/examples/celery/tasks.py#L8-L9).
- **Go** supports [Manual background job tracking](https://github.com/airbrake/gobrake#sending-queue-stats)
- Don't see your library? Let us know [support@airbrake.io](mailto:support.io)!

### Questions?

{% include_relative partials/faq.md %} You can also reach us at
[support@airbrake.io](mailto:support@airbrake.io). Our team is happy to answer
questions and we are always accepting feedback.
