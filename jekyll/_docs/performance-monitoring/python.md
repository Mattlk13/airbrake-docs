---
layout: classic-docs
title: Performance Monitoring for Python apps
short-title: Monitoring Python apps
categories: [performance-monitoring]
group: Python Performance Monitoring
description: Performance Monitoring for Python
---

{% include_relative partials/features-list.md %}

## Python Support

**Python support for Performance Monitoring is currently in early access**

Airbrake Performance Monitoring for Python supports:
- [Django](/docs/performance-monitoring/django/)
- [Flask](/docs/performance-monitoring/flask/)
- Manual tracking via API (more info below)

## Tracking Performance manually

Not using the Django or Flask frameworks? Track performance manually by using
the following API:

## Sending route stats

`notifier.routes.notify` allows sending route stats to Airbrake. The library
provides integrations with Django and Flask. (your routes are tracked
automatically). You can also use this API manually:

```py
import pybrake.RouteMetric as RouteMetric

metric = RouteMetric(method=request.method, route=route)
metric.status_code = response.status_code
metric.content_type = response.headers.get("Content-Type")
metric.end_time = time.time()

notifier.routes.notify(metric)
```

## Sending route breakdowns

`notifier.routes.breakdowns.notify` allows sending performance breakdown stats
to Airbrake. You can use this API manually:

```py
import pybrake.RouteBreakdowns as RouteBreakdowns

metric = RouteBreakdowns(method=request.method, route=route)
metric.response_type = response.headers.get("Content-Type")
metric.end_time = time.time()

notifier.routes.notify(metric)
```

## Sending query stats

`notifier.queries.notify` allows sending SQL query stats to Airbrake. The
library provides integration with Django (your queries are tracked
automatically). You can also use this API manually:

```py
import pybrake.QueryStat as QueryStat

metric = QueryStat(
  method=request.method,
  route=route,
  query="SELECT * FROM foos"
)
metric.end_time = time.time()

notifier.queries.notify(metric)
```

## Sending queue stats

`notifier.queues.notify` allows sending queue (job) stats to Airbrake. The
library provides integration with Celery (your queues are tracked
automatically). You can also use this API manually:

```py
import pybrake.QueueMetric as QueueMetric

metric = QueryMetric(queue="foo_queue")
notifier.queues.notify(metric)
```

{% include_relative partials/congratulations.md %}

### Want to learn more?

Want to learn more about pybrake? Check out [our official GitHub repo](https://github.com/airbrake/pybrake).
