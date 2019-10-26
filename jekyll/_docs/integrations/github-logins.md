---
layout: classic-docs
title: GitHub logins
categories: [integrations]
description: GitHub Logins
---

## Overview
Airbrake supports using your GitHub account to log in to Airbrake.

## How to link your GitHub account
You can link your GitHub account to your Airbrake account from
[your profile settings page](https://airbrake.io/users/edit).

### Enable GitHub logins
![github logins enabled button](/docs/assets/img/docs/integrations/github_logins_enable_button.png)

You can also enable GitHub logins from the Airbrake login page. To do this,
just select the "Sign in with GitHub" button from the
[login page](https://airbrake.io/login) and follow the instructions.

![github logins sign in page](/docs/assets/img/docs/integrations/github_logins_sign_in_page.png)

## Security options
Airbrake allows you to require that all users in your Airbrake account use
GitHub authentication to log in to Airbrake. When this setting is enabled, no
users in your account will be able to log in using their email and password.
Instead they will be required to use GitHub authentication to sign in.

This option allows users to take advantage of
[GitHub's two factor authentication](https://help.github.com/articles/about-two-factor-authentication/)
to secure their Airbrake accounts.

You can find this option in your
[account security settings](https://airbrake.io/account/security)

## Troubleshooting
**Error: "You don't have access to this Airbrake account because you're not a member of `'YOUR_GITHUB_ORG_NAME'`
GitHub organization".**

Revoke Airbrake access on GitHub [(https://github.com/settings/applications)](https://github.com/settings/applications)
and try to log in again. You will be asked to approve authorization again and then
you should grant access for `'YOUR_GITHUB_ORG_NAME'` GitHub organization.
