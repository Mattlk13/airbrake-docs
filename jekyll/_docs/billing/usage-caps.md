---
layout: classic-docs
title: Usage caps
categories: [billing]
description: Usage caps
---

- Airbrake plans have pre-paid error/performance quotas along with on-demand
  errors/events
- Errors and performance events beyond your monthly plan quota will be charged
  on a usage basis
- A monthly cap can be set to prevent additional errors from being processed
  beyond that number
  - This cap can be set for your entire account, and/or independently for each
    project
  - Example: A cap can be set for a non-critical project (like a staging
    environment), while still allowing all errors from mission-critical projects
    to be processed
- To set a monthly error cap for a project or the entire account, go to "Account
  & Billing" and select the "Usage caps" tab
  ![usage-caps](/docs/assets/img/docs/usage-caps.png)
  - Once the cap is reached, no additional errors/events will be accepted until
  the start of the next billing cycle
- Filters in the notifier can be set to ignore specific low-priority errors
  and/or known errors that aren’t intended to be fixed.
- Filters can also be used to send a subset of a specific error or type of error
  \- lowering usage while maintaining visibility into application performance
