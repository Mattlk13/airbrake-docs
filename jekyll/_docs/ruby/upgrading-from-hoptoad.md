---
layout: classic-docs
title: Upgrading from Hoptoad
categories: [ruby]
description: Upgrading from Hoptoad
---

The old Hoptoad gem is no longer supported. To get all the latest features and
fixes, you should upgrade to the latest version of our gem.

### Step 1: Uninstall the old Hoptoad notifier

Uninstall the old Hoptoad notifier by removing it from your Gemfile, then run
the command:

```
bundle install
```

You should also replace references in your app to `HoptoadNotifier` to
`Airbrake`. For example:

```rb
# Old name
HoptoadNotifier.notify(err)

# Current name
Airbrake.notify(err)
```

Upgrade to the latest version of our gem by updating your Gemfile:

```rb
gem 'airbrake'
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
