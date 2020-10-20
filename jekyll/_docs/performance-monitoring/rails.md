---
layout: classic-docs
title: Performance Monitoring for Rails applications
short-title: Monitoring Rails apps
categories: [performance-monitoring]
group: Rails Performance Monitoring
group-position: 1
description: Performance Monitoring for Rails apps
---

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

### Step 2: Update your config file

Check your `config/initializers/airbrake.rb` file to make sure the
`performance_stats` options is set to `true`.

```rb
Airbrake.configure do |c|
  c.performance_stats = true
end
```

{% include_relative partials/congratulations.md %}

### Upgrading from a previous gem version?

If you are upgrading from a previous version of our gem, please follow [our
upgrade guide](/docs/ruby/upgrading-your-notifier/) to get started with
Performance Monitoring.
