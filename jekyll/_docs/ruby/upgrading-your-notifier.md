---
layout: classic-docs
title: Upgrading your notifier
short-title: Updating your Rails notifier
categories: [ruby, performance-monitoring]
group: Rails Performance Monitoring
group-position: 2
description: Upgrading your notifier
---
> **Note:** If you are upgrading from version `4.X.X` or older, please
follow our [guide to upgrade from a deprecated version](/docs/ruby/upgrading-from-deprecated-versions/).

**Step 1:** To upgrade to the latest version of the
[airbrake gem](https://github.com/airbrake/airbrake)
just edit your `Gemfile`:

```rb
gem 'airbrake'
```

**Step: 2:** Run the update command to update the `airbrake` gem and `airbrake-ruby` gem
it depends on:

```
bundle update airbrake airbrake-ruby
```

That's it! Your upgrade is complete.

#### Problems upgrading?
If you run into any issues upgrading, we are happy to help. Just let us
know what happened at [support@airbrake.io](mailto:support@airbrake.io).

#### Going further
Check out our
[main gem's GitHub](https://github.com/airbrake/airbrake)
for more info or our base, Ruby gem for
[advanced configuration options](https://github.com/airbrake/airbrake-ruby).
