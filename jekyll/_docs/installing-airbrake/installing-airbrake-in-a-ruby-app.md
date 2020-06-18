---
layout: classic-docs
title: Installing Airbrake in a Ruby app
short-title: Ruby
language: ruby
categories: [installing-airbrake]
description: Installing Airbrake in a Ruby app
---

![ruby flag](/docs/assets/img/docs/ruby_flag.jpeg)

### Features
* Simple to install and configure
* Automatic reporting of unhandled exceptions
* Ignore specific errors and filter out sensitive information
* Add extra context to errors before they are sent
* Set error severity and control notification thresholds

[See all features](https://github.com/airbrake/airbrake-ruby#introduction)

### Install with bundler

Add the Airbrake Ruby gem to your Gemfile and run `bundle install`:

```ruby
gem 'airbrake-ruby'
```

### Manual installation

Invoke the following command from your terminal:

```bash
gem install airbrake-ruby
```

### Configuration

This is the minimal example that you can use to test Airbrake Ruby with your
project. You can find your `PROJECT ID` and `PROJECT API KEY` available from
with your project's settings page.

```ruby
require 'airbrake-ruby'

# Every Airbrake notifier must configure
# two options: `project_id` and `project_key`.
Airbrake.configure do |c|
  c.project_id = <Your project ID>
  c.project_key = '<Your project API KEY>'
end

# Asynchronous error delivery.
begin
  1/0
rescue ZeroDivisionError => ex
  # Return value is always `nil`.
  Airbrake.notify(ex)
end

puts 'A ZeroDivisionError was sent to Airbrake asynchronously!',
     "Find it at your project's dashboard on https://airbrake.io"

# Synchronous error delivery.
begin
  1/0
rescue ZeroDivisionError => ex
  # Return value is a Hash.
  response = Airbrake.notify_sync(ex)
end

puts "Another ZeroDivisionError was sent to Airbrake synchronously!",
     "See it at #{response['url']}!"
```

### Going further
For advanced configuration options like
[ignoring errors](https://github.com/airbrake/airbrake-ruby#airbrakeadd_filter),
[adding extra context](https://github.com/airbrake/airbrake-ruby#airbrakenotify),
and [filtering sensitive information](https://github.com/airbrake/airbrake-ruby#blocklist_keys)
please visit our [official GitHub repo](https://github.com/airbrake/airbrake-ruby).
