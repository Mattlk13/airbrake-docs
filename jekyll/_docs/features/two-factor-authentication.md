---
layout: classic-docs
title: Two-factor authentication
categories: [features]
description: Two-factor authentication
---

Two-factor authentication (2FA) adds an extra layer of security to ensure no one
outside your organization can gain access to your Airbrake account and the error
data you've sent.

Two-factor authentication is available on [all paid plans](https://airbrake.io/pricing).

### How to start using the two-factor authentication

Simply enable it from your [profile page](https://airbrake.io/users/edit) by
clicking the "Enable" button next to the "Two-factor authentication" setting
title:

![2fa-enable](/docs/assets/img/docs/features/2fa_enable.png)

After that, you will be asked to scan the QR code with a 2FA app (e.g.,
[Google Authenticator](https://play.google.com/store/apps/details?id=com.google.android.apps.authenticator2),
[Authy](https://authy.com/), [1Password](https://1password.com/) or other
similar apps) and provide the 6-digit authentication code to verify that you
enabled the 2FA successfully. You can also manually enter the key if there are
issues scanning the QR code.

![2fa-enable-qr-code](/docs/assets/img/docs/features/2fa_enable_qr_code.png)

Once you've successfully entered the 6-digit auth code, 2FA will be enabled -
but there's one more critical step!

In the event you lose access to your device and can't receive 2FA codes,
"recovery codes" can be used to regain login access to your Airbrake account.
So it's important to keep these codes protected and accessible in a safe place,
like in your password manager (we use 1Password for ours).

![2fa-enable-recovery-codes](/docs/assets/img/docs/features/2fa_enable_recovery_codes.png)

With the setup done, on the next login, you will be asked to input the
two-factor authentication code from your 2FA app.

![2fa-login](/docs/assets/img/docs/features/2fa_login.png)


### Require two-factor authentication

On your [Airbrake account security page](https://airbrake.io/account/security),
you can enable the **Require all users to have two-factor authentication enabled**
setting which forces all users on your Airbrake account to enable two-factor
authentication. Users won't have access to any Airbrake page until they enable
it. Additionally, if an admin user on your account disables that setting, all
other admin users will be notified about disabled setting via email.

![require-2fa-setting](/docs/assets/img/docs/features/require-2fa-setting.png)
