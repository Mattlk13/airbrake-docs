---
layout: classic-docs
title: Installing Airbrake in a Flask app
short-title: Flask
language: flask
categories: [installing-airbrake]
description: installing airbrake in a Flask app
---

![python flag](/docs/assets/img/docs/python_flag.jpeg)

## Features
* Simple to install and configure
* Add extra context to errors before they are sent
* Set error severity and control notification thresholds
* Compatible with [Airbrake On-Premise](https://airbrake.io/enterprise)

{% include flask-install.md %}

## Sending errors to Airbrake

```py
try:
    raise ValueError('hello')
except Exception as err:
    notifier.notify(err)
```

For more information, check out [pybrake's official GitHub
repo](https://github.com/airbrake/pybrake#flask-integration).
