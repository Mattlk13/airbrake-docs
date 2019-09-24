---
layout: classic-docs
title: Configuring project environments
categories: [airbrake-faq]
description: configuring project environments
---

You can configure environments in your Airbrake project for organizing your
project's errors.  Each project can have as many environments as you like.
Some examples of commonly used environments are `production`, `staging`,
`development`, and `test`.

![project environments](/docs/assets/img/docs/project_environments.png)

## Setting your environments
Setting your environments is done in your notifier configuration.  The setup is
different for each notifier so check your notifier's readme on GitHub.

#### Examples for our most popular languages
- [Ruby/Rails](https://github.com/airbrake/airbrake-ruby#environment)
- [JavaScript](https://github.com/airbrake/airbrake-js/tree/master/packages/browser#filtering-errors)
- [Angular](https://github.com/airbrake/airbrake-js/tree/master/packages/browser#filtering-errors)
- [PHP](https://github.com/airbrake/phpbrake#adding-custom-data-to-the-notice)
- [Python](https://github.com/airbrake/airbrake-python#setup)
- [.NET](https://github.com/airbrake/SharpBrake#usage)
- [Java](https://github.com/airbrake/javabrake#quickstart)
- [Node.js](https://github.com/airbrake/airbrake-js/tree/master/packages/browser#filtering-errors)
- [Golang](https://github.com/airbrake/gobrake#example)
- [Django](https://github.com/airbrake/airbrake-django#configure-airbrake-in-your-settingspy)
