---
layout: classic-docs
title: Configuring notifications
categories: [airbrake-faq]
description: configuring notifications
---

## What settings are available per project?

### **Notify on error**
You will be notified whenever a new exception group is created or an error
group becomes unresolved.

### **Notify on comments**
You will be notified when another team member comments on an exception

### **Production environment only**
Only receive notifications from errors that occur in the `production`
environment.

### **Automatically subscribe to new projects**
When a new project is added you will be subscribed to that project
automatically. **This option is only available to admins on the account**

### Notes

- These settings are user specific.
- These settings only affect email notifications. They will not affect your
  Slack or Flowdock integrations as those are setup per project.*
- The environment needs to be `production` (case independent). eg: `Production`
  is a production environment while `production_US` and `prod` are not a
  production environments.

## Modify your notification settings

### Open the **upper right dropdown** under your user name and click **profile & notifications**
Or click [https://airbrake.io/users/notifications](https://airbrake.io/users/notifications) to be
taken to your Profile & Notifications settings.

![airbrake dropdown profile & notifications](/docs/assets/img/docs/airbrake/dropdown_profile_and_notifications.png)

### Tune your notification settings and **Save**

![airbrake notification settings](/docs/assets/img/docs/airbrake/notification_settings.png)
