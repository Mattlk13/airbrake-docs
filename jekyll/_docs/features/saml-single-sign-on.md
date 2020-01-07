---
layout: classic-docs
title: SAML single sign-on (beta)
short-title: SAML single sign-on (beta)
categories: [features]
description: SAML single sign-on
---

SAML single sign-on allows your team to log in via [Okta](https://www.okta.com)
or [OneLogin](https://www.onelogin.com). This feature is currently in beta.
Please contact [support@airbrake.io](mailto:support@airbrake.io) if you want to
be a beta tester.

_**Note:** Single sign-on is a premium feature available to all accounts on our
Business plan ($599/month) and larger._

Below you can find the configuration documentation for Okta and OneLogin.

## Okta

### Configuration

1. On your [Airbrake account security page](https://airbrake.io/account/security)
click on **Enable SAML** button:
![airbrake-enable-saml-btn](/docs/assets/img/docs/features/saml/airbrake-enable-saml-btn.png)

2. Copy **SAML Endpoint URL**:
![airbrake-copy-saml-endpoint](/docs/assets/img/docs/features/saml/airbrake-copy-saml-endpoint.png)

3. From your Okta account, find Airbrake.io and add it:
![okta-add-airbrake](/docs/assets/img/docs/features/saml/okta-add-airbrake.png)

4. Paste copied SAML Endpoint URL to **SAML Endpoint URL** input on
**Sign-On Options** tab:
![okta-saml-endpoint-url](/docs/assets/img/docs/features/saml/okta-saml-endpoint-url.png)

5. From the same tab copy **Identity Provider metadata** URL:
![okta-copy-metadata-url](/docs/assets/img/docs/features/saml/okta-copy-metadata-url.png)

6. Go back to Airbrake and paste copied metadata URL to **SAML/IdP Metadata URL** input,
and then click on **Enable SAML SSO** button:
![airbrake-metadata-url](/docs/assets/img/docs/features/saml/airbrake-metadata-url.png)

7. On Okta, click on **Done** button, visit **Assignments** tab, click on **Assign**
dropdown menu, and then click on **Assign to People**:
![okta-assign-to-people](/docs/assets/img/docs/features/saml/okta-assign-to-people.png)

8. For each user on Okta click on **Assign** button, change the email in
**User Name** input to match with the email on Airbrake for that user:
![okta-assign-to-user](/docs/assets/img/docs/features/saml/okta-assign-to-user.png)

### Sign in with Okta

Now you can log to Airbrake from Okta or from Airbrake via Okta:
![airbrake-sso-btn](/docs/assets/img/docs/features/saml/airbrake-sso-btn.png)

### Require SAML single sign-on

After you have successfully authenticated via Okta for the first time, you can
enable **Require SAML single sign-on** setting which will allow only logins via
Okta to your Airbrake account:
![airbrake-require-saml](/docs/assets/img/docs/features/saml/airbrake-require-saml.png)


## OneLogin

### Configuration

1. On your [Airbrake account security page](https://airbrake.io/account/security)
click on **Enable SAML** button:
![airbrake-enable-saml-btn](/docs/assets/img/docs/features/saml/airbrake-enable-saml-btn.png)

2. Copy **SAML Endpoint URL**:
![airbrake-copy-saml-endpoint](/docs/assets/img/docs/features/saml/airbrake-copy-saml-endpoint.png)


3. From your OneLogin account, find Airbrake.io and add it:
![onelogin-add-airbrake](/docs/assets/img/docs/features/saml/onelogin-add-airbrake.png)

4. Paste copied SAML Endpoint URL to **ACS URL** input on **Configuration** tab,
and then click on **Save** button:
![onelogin-acs-url](/docs/assets/img/docs/features/saml/onelogin-acs-url.png)

5. From the **SSO** tab copy **Issuer URL**:
![onelogin-metadata-url](/docs/assets/img/docs/features/saml/onelogin-metadata-url.png)

6. Go back to Airbrake and paste copied metadata URL to **SAML/IdP Metadata URL** input,
and then click on **Enable SAML SSO** button:
![airbrake-metadata-url](/docs/assets/img/docs/features/saml/airbrake-onelogin-metadata-url.png)

7. From OneLogin, visit **Users** tab. For each user on OneLogin change the email
in **Name ID Value** input to match with the email on Airbrake for that user:
![onelogin-assign-to-user](/docs/assets/img/docs/features/saml/onelogin-assign-to-user.png)

### Sign in with OneLogin

Now you can log to Airbrake from OneLogin or from Airbrake via OneLogin:
![airbrake-sso-btn](/docs/assets/img/docs/features/saml/airbrake-sso-btn.png)

### Require SAML single sign-on

After you have successfully authenticated via OneLogin for the first time, you can
enable **Require SAML single sign-on** setting which will allow only logins via
OneLogin to your Airbrake account:
![airbrake-require-saml](/docs/assets/img/docs/features/saml/airbrake-require-saml.png)
