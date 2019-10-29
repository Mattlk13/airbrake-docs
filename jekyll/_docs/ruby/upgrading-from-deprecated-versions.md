---
layout: classic-docs
title: Upgrading from deprecated versions
categories: [ruby]
description: Upgrading from deprecated versions
---

Support for version 4 of our gem [ended November
2016](https://github.com/airbrake/airbrake/issues/596). If your app is using
version or earlier, we would recommend upgrading to a currently supported
version using the guide below.

### Step 1: Update your gems

Upgrade to the latest version of our gem by updating your Gemfile:

_**Note:** our gem is
updated frequently, you can always find the current version on
[RubyGems](https://rubygems.org/gems/airbrake) or on [our
GitHub](https://github.com/airbrake/airbrake/releases)._

```rb
gem 'airbrake', '~> 9.5'
```

Then run the update command to update our main gem and the `airbrake-ruby` gem
it uses:

```
bundle update airbrake airbrake-ruby
```

### Step 2: Regenerate config

Run generate command to overwrite old Airbrake config (make sure to replace
`PROJECT_ID` and `API_KEY` with your project's actual values which can be found
in your project settings page):

```
rails generate airbrake PROJECT_ID API_KEY
```

To overwrite your old config, answer `Y` when prompted:

```
$ rails generate airbrake PROJECT_ID API_KEY
    conflict  config/initializers/airbrake.rb
Overwrite /Users/arthur/my-app/config/initializers/airbrake.rb? (enter "h" for help) [Ynaqdhm]
```

For a full migration guide, check out
[our doc on GitHub](https://github.com/airbrake/airbrake/blob/master/docs/Migration_guide_from_v4_to_v5.md).

_**Note:** by default, current versions of our gem monitor performance along
with errors. If you want to disable performance monitoring, set [the
`performance_stats`
option](https://github.com/airbrake/airbrake-ruby#performance_stats) to
`false`._
