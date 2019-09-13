---
layout: classic-docs
title: Performance Monitoring for Flask apps
short-title: Performance Monitoring for Flask
categories: [performance-monitoring]
description: Performance Monitoring for Flask
---

Application Performance Monitoring with Airbrake makes it easy to:
- See a broad performance overview for your whole application
- Measure user satisfaction with your app performance using Apdex
- Identify routes with problematic performance
- Zoom into specific endpoints to see time spent in the DB, view, cache,
  external requests, and more

## Flask Support

**Flask support for Performance Monitoring is currently in early access**

The `pybrake` package makes it quick and easy to monitor your Flask app's
performance. It only takes a few minutes to start collecting real performance
data so let's jump right in!

## Step 1: Install the latest version of pybrake

{% highlight bash %}
pip install pybrake
{% endhighlight %}

## Step 2: Configure the Airbrake Flask middleware

Replace the placeholder `project_id` and `project_key` values from the example
below with the real values from your project's setting page.

{% highlight python %}
from flask import Flask
import pybrake.flask

app = Flask(__name__)
app.config['PYBRAKE'] = dict(
    project_id=123123,
    project_key='FIX-ME',
)
app = pybrake.flask.init_app(app)


@app.route('/')
def hello_world():
    return 'Hello, World'
{% endhighlight %}

Once you run this example and perform some `curl`s or visit
[localhost:5000](http://localhost:5000/) in your browser, you will see
performance requests in your project's performance dashboard.

## Congratulations!

Great job! Just visit your Airbrake project's Performance Dashboard to see route
data for your app. Soon enough you'll have more insights into your application's
performance. In the meantime why not check out the [Performance Dashboard
features](/docs/performance-monitoring/performance-dashboard-features/). If you
have questions about Performance Monitoring, visit the [Performance Monitoring
FAQ](/docs/performance-monitoring/frequently-asked-questions/).

### Want to learn more?

Want to learn more about pybrake? Check out [our official GitHub repo](https://github.com/airbrake/pybrake).
