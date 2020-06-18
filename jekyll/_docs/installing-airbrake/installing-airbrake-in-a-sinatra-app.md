---
layout: classic-docs
title: Installing Airbrake in a Sinatra app
short-title: Sinatra
language: sinatra
categories: [installing-airbrake]
description: Installing Airbrake in a Sinatra app
---

![ruby flag](/docs/assets/img/docs/ruby_flag.jpeg)

### Features
* Simple to install and configure
* Automatic reporting of unhandled exceptions
* Ignore specific errors and filter out sensitive information
* Append extra information from requests before sending to Airbrake
* Set error severity and control notification thresholds

View the full list of features [on GitHub](https://github.com/airbrake/airbrake-ruby#introduction).

### Install with bundler

Add the Airbrake Ruby gem to your Gemfile and run `bundle install`:

```ruby
gem 'airbrake'
```

### Manual installation

Invoke the following command from your terminal:

```bash
gem install airbrake
```

### Configuration

To send exceptions to Airbrake from a Sinatra application, simply `use` our Rack
middleware, and configure with your `PROJECT ID` and `PROJECT API KEY` available
from [your project's settings
page](https://github.com/airbrake/airbrake-ruby#config-options).

```ruby
# sinatra-airbrake-example.rb
require 'sinatra/base'
require 'airbrake'

Airbrake.configure do |c|
  c.project_id = '<Your project ID>'
  c.project_key = '<Your project API KEY>'

  # Display debug output.
  c.logger.level = Logger::DEBUG
end

class MyApp < Sinatra::Base
  use Airbrake::Rack::Middleware

  get('/') { 1/0 }
end

run MyApp.run!
```

### Going further
For advanced configuration options like
[ignoring errors](https://github.com/airbrake/airbrake-ruby#airbrakeadd_filter),
[adding extra context](https://github.com/airbrake/airbrake-ruby#airbrakenotify),
[appending info from requests](https://github.com/airbrake/airbrake#appending-information-from-rack-requests),
[filtering sensitive information](https://github.com/airbrake/airbrake-ruby#blocklist_keys),
and more please visit the
[airbrake-ruby](https://github.com/airbrake/airbrake-ruby) and
[airbrake](https://github.com/airbrake/airbrake#sinatra) GitHub repos.
