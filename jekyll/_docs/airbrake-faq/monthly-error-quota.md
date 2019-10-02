---
layout: classic-docs
title: Monthly error quota
categories: [airbrake-faq]
description: Monthly error quota
---

Your plan's monthly error quota determines the number of errors that can be sent
to your Airbrake account within a billing period. Your monthly error
quota is refilled at the beginning of each new billing period.

### Usage alerts
Airbrake will automatically notify you when your monthly error quota reaches
certain thresholds.
You will also be notified if you completely run out of your monthly error quota
and need to take action.

### Running out of errors
If you suspect you will run out of errors before your monthly quota is refilled,
we recommend [reducing your error quota usage](/docs/airbrake-faq/reducing-error-quota-usage/) or
[upgrading to increase your quota](https://airbrake.io/account/plan/edit).

If you completely deplete your monthly error quota, Airbrake will stop accepting
errors until you [upgrade your plan](https://airbrake.io/account/plan/edit) or the
next billing cycle starts. Upgrading your plan will increase your current
monthly error quota and errors will be accepted again immediately.

### Setting a rate limit
Setting a rate limit controls how many errors will be accepted each minute for
your account. Errors reported that exceed your configured rate limit will be
discarded.

For example, if you set your rate limit to 100 errors/min, then you report 120
errors at 12:03 pm, the first 100 errors would be accepted and the last 20
errors would be discarded. Your account would start accepting new errors at
12:04 pm.

You can set your rate limit to any value. If you only want to protect against
using too much of your error quota during a large, unexpected spike, then you
might want to use a high value (eg: in the thousands) for a rate limit. If you
want to maximize preserving your error quota through out the month, then you
might want to use a lower value.

Any account admin can configure the max errors per minute from the
[account settings](https://airbrake.io/account/adjust-rate-limit) page.

### Why monthly error quota?
Our [blog post](https://airbrake.io/blog/airbrake-news/get-more-flexibility-with-monthly-error-quotas)
outlines the benefits a monthly error quota has over a rate limit that resets
each minute.
