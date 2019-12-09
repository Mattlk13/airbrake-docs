---
layout: classic-docs
title: Digest emails
categories: [features]
description: A glimpse of what happened on your account over a period of time emailed to you on a regular basis
---

Digest emails provide a summary of what happened on your account, including new
errors, occurrences, deploys, and performance stats across all projects you are
subscribed to. The summary contains trends to help you understand how your
projects are performing.

For example, the following digest shows a 250% increase of errors during one day
in 88 projects an account has (7 errors yesterday vs 2 errors 2 days ago):

![digest email](/docs/assets/img/docs/features/digest.png)

The information is emailed to you in stated intervals (currently, we support
only the daily interval).

# <a name="managing-email-subscriptions"></a> Managing email subscriptions

To unsubscribe from daily digests, click the "Unsubscribe" link and follow the
instructions:

![digest emails unsubscribe](/docs/assets/img/docs/features/digest_unsubscribe.png)

Alternatively, you can configure the ["Send digest emails"
setting](/docs/features/digests/#managing-email-subscriptions) in
your [profile notifications](https://airbrake.io/users/notifications):

![digest emails option](/docs/assets/img/docs/features/digest_settings.png)

Digest emails collect information based on your project subscriptions. For
example, if your account has 3 projects and you are subscribed only to 2 of
them, then your digest won't be taking into account the 3rd project that you
don't belong to. You can manage your project subscriptions at the ["Edit
projects" page](https://airbrake.io/users/projects).
