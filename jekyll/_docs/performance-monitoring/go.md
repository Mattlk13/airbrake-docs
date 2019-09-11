---
layout: classic-docs
title: Performance Monitoring for Go applications
short-title: Performance Monitoring for Go
categories: [performance-monitoring]
description: Performance Monitoring for Go applications
---

Application Performance Monitoring with Airbrake makes it easy to:
- See a broad performance overview for your whole application
- Measure user satisfaction with your app performance using Apdex
- Identify routes with problematic performance
- Zoom into specific endpoints to see time spent in the DB, view, cache,
  external requests, and more

## Go Support

**Go support for Performance Monitoring is currently in early access** and
features:
- Sending route stats
- HTTP middlewares for Gin and Beego users
- Wrapping important code blocks for detailed timing
- Collecting stats about individual SQL queries

## Step 1: Install the latest version of gobrake

{% highlight bash %}
go get github.com/airbrake/gobrake
{% endhighlight %}

## Step 2: Configure gobrake and start sending route stats

Before you can send performance stats replace the placeholder `ProjectId` and
`ProjectKey` values from the example below with the real values from your
project's setting page.

Now that your gobrake notifier is configured let's collect some routes stats, we
will use a simple net/http middleware in this example.

> **Note**: If you use **Gin** or **Beego**, gobrake provides middleware out of
the box and you may find our example apps more helpful:
[Gin example](https://github.com/airbrake/gobrake/tree/master/examples/gin),
[BeeGo example](https://github.com/airbrake/gobrake/tree/master/examples/beego).

{% highlight go %}
package main

import (
  "fmt"
  "net/http"

  "github.com/airbrake/gobrake"
)

// Airbrake is used to report errors and track performance
var Airbrake = gobrake.NewNotifierWithOptions(&gobrake.NotifierOptions{
  ProjectId: 123123,               // <-- Fill in this value
  ProjectKey: "YourProjectAPIKey", // <-- Fill in this value
  Environment: "Production",
})

func indexHandler(w http.ResponseWriter, req *http.Request) {
  fmt.Fprintf(w, "Hello, There!")
}

func main() {
  fmt.Println("Server listening at http://localhost:5555/")
  // Wrap the indexHandler with Airbrake Performance Monitoring middleware:
  http.HandleFunc(airbrakePerformance("/", indexHandler))
  http.ListenAndServe(":5555", nil)
}

func airbrakePerformance(route string, h http.HandlerFunc) (string, http.HandlerFunc) {
  handler := http.HandlerFunc(func(w http.ResponseWriter, req *http.Request) {
    ctx := req.Context()
    ctx, routeMetric := gobrake.NewRouteMetric(ctx, req.Method, route) // Starts the timing
    arw := newAirbrakeResponseWriter(w)

    h.ServeHTTP(arw, req)

    routeMetric.StatusCode = arw.statusCode
    Airbrake.Routes.Notify(ctx, routeMetric) // Stops the timing and reports
    fmt.Printf("code: %v, method: %v, route: %v\n", arw.statusCode, req.Method, route)
  })

  return route, handler
}

type airbrakeResponseWriter struct {
  http.ResponseWriter
  statusCode int
}

func newAirbrakeResponseWriter(w http.ResponseWriter) *airbrakeResponseWriter {
  // Returns 200 OK if WriteHeader isn't called
  return &airbrakeResponseWriter{w, http.StatusOK}
}

func (arw *airbrakeResponseWriter) WriteHeader(code int) {
  arw.statusCode = code
  arw.ResponseWriter.WriteHeader(code)
}
{% endhighlight %}

Once you run this example and perform some `curl`s or visit
[localhost:5555/](http://localhost:5555/) in your browser, you will see
performance requests in your project's performance dashboard.

## Congratulations!

Great job! If you've used this example in your app, you can visit your
Airbrake project's Performance Dashboard to see your performance data! Soon
enough you'll have more insights into your application's performance. In the
meantime why not check out the [Performance Dashboard
features](/docs/performance-monitoring/performance-dashboard-features/).
If you have questions about Performance Monitoring, visit the [Performance
Monitoring FAQ](/docs/performance-monitoring/frequently-asked-questions/).

### Measuring timing of specific operations

Need more visibility into a slow route? To get more detailed timing, you
can wrap important blocks of code into spans. For example, you can create 2
spans `sql` and `http` to measure timing of specific operations:

{% highlight go %}
metric := &gobrake.RouteMetric{
    Method: c.Request.Method,
    Route: routeName,
    StartTime: time.Now(),
}

metric.StartSpan("sql")
users, err := fetchUser(ctx, userID)
metric.EndSpan("sql")

metric.StartSpan("http")
resp, err := http.Get("http://example.com/")
metric.EndSpan("http")

metric.StatusCode = http.StatusOK
notifier.Routes.Notify(ctx, metric)
{% endhighlight %}

### Want to learn more?

Want to learn more about gobrake? Check out [our official GitHub repo](https://github.com/airbrake/gobrake).
