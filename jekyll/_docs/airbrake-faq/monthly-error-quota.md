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

### Running out of errors
If you exceed your account's error quota, additional errors will be charged an
"on-demand" rate based on your selected plan.

### Can I control error volume to avoid on-demand charges?
Yes, you can set a "usage cap" for your account and for individual projects.
This setting enables you to specify exacty how many errors you want to see each
billing cycle. Setting the Usage Cap to an amount greater than your plan quota
will mean that you will see On-Demand Errors until you reach the "capped" usage
limit for each project or account.

If you set your Usage Cap equal to the quota of your base Airbrake plan, and you
exceed your account's error quota, no more errors will be accepted until your
next billing cycle begins. You will receive alerts if you get close to exceeding
your monthly quota.

At any point in time you can adjust the usage caps for your account (up or down)
or check your current usage via the Account & Billing section of your Airbrake
Dashboard: [https://airbrake.io/account/edit](https://airbrake.io/account/edit).

Read more about [Usage caps](/docs/billing/usage-caps).
