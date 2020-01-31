---
layout: classic-docs
title: Performance Monitoring Getting Started
short-title: Getting Started
categories: [performance-monitoring]
group: About Performance Monitoring
group-position: 1
description: Getting Started with Performance Monitoring
---

{% include_relative partials/features-list.md %}

## Supported languages
- Rails (instructions below)
- [Node.js (Express.js) setup guide](/docs/performance-monitoring/updating-your-node-notifier/)
- [Go setup guide](/docs/performance-monitoring/go/)
- [Django setup guide](/docs/performance-monitoring/django/)
- [Flask documentation](/docs/performance-monitoring/flask/)

## Rails installation

Performance Monitoring is built into the same notifier you use to report errors
from your application. To start sending performance data for your app to
Airbrake just install or upgrade the Airbrake gem to the latest version.

### Step 1: Install the latest version of the Airbrake gem

Add the Airbrake gem to your `Gemfile`:

```ruby
gem 'airbrake'
```

To integrate Airbrake with your Rails application, invoke the following command
and replace `PROJECT_ID` and `PROJECT_KEY` with your project's values:

```shell
rails g airbrake PROJECT_ID PROJECT_KEY
```

{% include_relative partials/congratulations.md %}

### Upgrading from a previous gem version?

If you are upgrading from a previous version of our gem, please follow [our
upgrade guide](/docs/ruby/upgrading-your-notifier/) to get started with
Performance Monitoring.
