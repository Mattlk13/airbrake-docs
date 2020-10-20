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
