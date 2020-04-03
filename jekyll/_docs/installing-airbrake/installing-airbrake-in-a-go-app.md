---
layout: classic-docs
title: Installing Airbrake in a Go app
short-title: Go
language: golang
categories: [installing-airbrake]
description: installing airbrake in a Go app
---

![Go flag](/docs/assets/img/docs/go_flag.jpeg)

### Features
* Notify Airbrake on panics
* Ignore errors based on class, message, status, file, or any other filter
* [Send errors from glog to Airbrake](https://github.com/airbrake/glog)
* Add extra context to errors before reporting them
* Set error severity to control notification thresholds

### Example usage

To include Airbrake in your Go application navigate to your project's main
directory and install our Go package, [gobrake][gobrake], using the `go get`
command:

```shell
go get github.com/airbrake/gobrake/v4
```

Note: gobrake requires [Go Modules][go-mod] support.

Next, follow the example below and make sure to obtain your `ProjectId` &
`ProjectKey` from your project's settings page.


```go
package main

import (
	"errors"

	"github.com/airbrake/gobrake/v4"
)

var airbrake = gobrake.NewNotifierWithOptions(&gobrake.NotifierOptions{
	ProjectId: 123456,
	ProjectKey: "FIXME",
	Environment: "production",
})

func main() {
	defer airbrake.Close()
	defer airbrake.NotifyOnPanic()

	airbrake.Notify(errors.New("operation failed"), nil)
}
```

### More info on GitHub
For more information on [ignoring
notices](https://github.com/airbrake/gobrake#ignoring-notices), [setting
severity](https://github.com/airbrake/gobrake#setting-severity), or our [glog
fork]() please visit our [official GitHub
repo](https://github.com/airbrake/gobrake).
Contributors always welcome!

[gobrake]: https://github.com/airbrake/gobrake
[go-mod]: https://github.com/golang/go/wiki/Modules
