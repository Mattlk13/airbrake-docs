---
layout: classic-docs
title: Upgrading your notifier
categories: [ruby]
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

> **Note:** by default, current versions of our gem **monitor performance** along
with errors. If you want to disable performance monitoring, set the
[`performance_stats`
option](https://github.com/airbrake/airbrake-ruby#performance_stats) to
`false`.

#### Problems upgrading?
If you run into any issues upgrading, we are happy to help. Just let us
know what happened at [support@airbrake.io](mailto:support@airbrake.io).
