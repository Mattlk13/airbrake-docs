---
layout: classic-docs
title: Updating your Go notifier
short-title: Updating your Go notifier
categories: [performance-monitoring]
description: How to update your Go notifier for Performance Monitoring
---

Get the most out of Airbrake's features and stay up to date with the latest
improvements by updating your project to the latest version of our Go error
reporting library.

## Step 1: Update your notifier

To update gobrake, run the following command:

```
go get -u github.com/airbrake/gobrake/v4
```

## Step 2: Add Performance Monitoring

Collect route stats automatically with our prepared middleware for:
- [Gin](https://github.com/airbrake/gobrake/blob/master/examples/gin)
- [Beego](https://github.com/airbrake/gobrake/blob/master/examples/beego)

Using the net/http middleware? Follow this example:

```go
package main

import (
  "fmt"
  "net/http"

  "github.com/airbrake/gobrake"
)

// Airbrake is used to report errors and track performance
var Airbrake = gobrake.NewNotifierWithOptions(&gobrake.NotifierOptions{
  ProjectId:   123123,              // <-- Fill in this value
  ProjectKey:  "YourProjectAPIKey", // <-- Fill in this value
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
```

To collect more finely grained timings, you can wrap important blocks in spans.
This example demonstrates how you can create two spans (`sql` and `http`) to
measure specific timings of those operations:

```go
metric := &gobrake.RouteMetric{
    Method: c.Request.Method,
    Route:  routeName,
    StartTime:  time.Now(),
}

metric.StartSpan("sql")
users, err := fetchUser(ctx, userID)
metric.EndSpan("sql")

metric.StartSpan("http")
resp, err := http.Get("http://example.com/")
metric.EndSpan("http")

metric.StatusCode = http.StatusOK
notifier.Routes.Notify(ctx, metric)
```

You can also collect stats about individual SQL queries performance using
following API:

```go
notifier.Queries.Notify(&gobrake.QueryInfo{
    Query:     "SELECT * FROM users WHERE id = ?", // query must be normalized
    Func:      "fetchUser", // optional
    File:      "models/user.go", // optional
    Line:      123, // optional
    StartTime: startTime,
    EndTime:   time.Now(),
})
```
