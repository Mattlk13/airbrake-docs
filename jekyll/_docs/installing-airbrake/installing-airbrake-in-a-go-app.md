---
layout: classic-docs
title: Installing Airbrake in a Go app
short-title: Go
language: golang
categories: [installing-airbrake]
description: installing airbrake in a Go app
---

![Go flag](/docs/assets/img/docs/go_flag.jpeg)

## Introduction

_Gobrake_ is the official notifier library for [Airbrake][airbrake] for the Go
programming language. Gobrake provides a minimalist API that enables the ability
to send any Go error or panic to the Airbrake dashboard. The library is
extremely lightweight, with minimal overhead.

## Key features

* Simple, consistent and easy-to-use library API
* Asynchronous exception reporting
* Flexible configuration options
* Support for environments
* Add extra context to errors before reporting them
* Filters support (filter out sensitive or unwanted data that shouldn't be sent)
* Ignore errors based on class, message, status, file, or any other filter
* SSL support (all communication with Airbrake is encrypted by default)
* Notify Airbrake on panics
* Set error severity to control notification thresholds
* Support for code hunks (lines of code surrounding each backtrace frame)
* Automatic deploy tracking
* Performance monitoring features such as HTTP route statistics, SQL queries,
	and Job execution statistics
* Integrations with Beego and Gin
* Last but not least, we follow semantic versioning 2.0.0
* [Send errors from glog to Airbrake](https://github.com/airbrake/glog)

## Installation

To include Airbrake in your Go application navigate to your project's main
directory and install our Go package, `gobrake`, using the `go get`
command:

```shell
go get github.com/airbrake/gobrake/v4
```

Next, import and initialize the `gobrake` package in your application:

```go
package main

import "github.com/airbrake/gobrake/v4"

var airbrake = gobrake.NewNotifierWithOptions(&gobrake.NotifierOptions{
	ProjectId: <YOUR PROJECT ID>,
	ProjectKey: "<YOUR API KEY>",
	Environment: "production",
})

func main() {
	defer airbrake.Close()
	defer airbrake.NotifyOnPanic()
}
```

To find `<YOUR PROJECT ID>` and `<YOUR API KEY>` navigate to your project's
Settings and copy the values from the right sidebar.

That's it! The `airbrake.NotifyOnPanic()` call will handle automatic panic reporting.

## Verify Airbrake is working as expected

You can use `airbrake.Notify()` to send handled errors. Let's use it now to
check if `gobrake` is installed correctly:

```go
import "errors"

func testAirbrake() {
	airbrake.Notify(errors.New("Error Test from Airbrake"), nil)
}
```

You should see your dashboard updating with your test error soon after you run
that function.

## Full documentation

Check out our [official GitHub repo][gobrake] for info on advanced features like
[ignoring errors][gobrake/ignore], [setting error severity][gobrake/severity]
and more.

[airbrake]: https://airbrake.io
[gobrake]: https://github.com/airbrake/gobrake
[gobrake/ignore]: https://github.com/airbrake/gobrake#ignoring-notices
[gobrake/severity]: https://github.com/airbrake/gobrake#setting-severity
