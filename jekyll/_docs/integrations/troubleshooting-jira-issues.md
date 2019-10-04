---
layout: classic-docs
title: Troubleshooting JIRA issues
categories: [integrations]
description: Troubleshooting JIRA issues
---

# Error 1: "Environment can't be set"

>400 Bad Request - Field 'environment' cannot be set. It is not on the appropriate screen, or unknown.

If you're integrating with a **next-gen JIRA project**, please visit
[this section](/docs/integrations/jira/#integrating-with-a-next-gen-jira-project).

This error arises when the **Environment** field is unavailable as an option
for JIRA issue creation.
The fix is to add the **Environment** field on your JIRA issue screen. These
next steps will help you add the **Environment field**.

## Steps

### 1. Click **Administration** in the top right corner and select **Issues**

![jira issues cog dropdown](/docs/assets/img/docs/integrations/jira_issues_cog_dropdown.png)

### 2. Select **Screens**

![jira issues admin dropdown](/docs/assets/img/docs/integrations/jira_issues_admin_dropdown.png)

### 3. In **Default Screen** under the **Operations** column click **Configure**
*Note: if you have changed your default screen, make sure to find the screen
that applies to your project.*

![jira issues default screen](/docs/assets/img/docs/integrations/jira_issues_default_screen.png)

### 4. Scroll to find the drop down menu and select **Environment**

![jira issues environment dropdown](/docs/assets/img/docs/integrations/jira_issues_environment_dropdown.png)

# Error 2: "Labels can't be set"

>400 Bad Request - Field 'labels' cannot be set. It is not on the appropriate screen, or unknown.

The solution for this error is nearly identical to the previous **Environment
can't be set** error except for one variation. The goal is to add a **Labels**
field on your JIRA issue screen. Follow the **Environment can't be set**
instructions above, but instead of adding **Environment** select **Labels**
from the dropdown menu.

If you are still experiencing this issue after adding **Labels** to your JIRA
issue screen. This can be caused by created a custom created field named
**Labels** instead of adding the default one provided by JIRA.
Please make sure to add the default **Labels** field.

# Error 3: "Summary can't be set"

>400 Bad Request - Field 'summary' cannot be set. It is not on the appropriate screen, or unknown.

The solution for this error is again identical to the **Environment can't be set**
and **Labels can't be set** errors. Follow the **Environment can't be set**
instructions above, but instead of adding **Environment** select **Summary**
from the dropdown menu.

Still seeing this error after following the steps above? If you use **Atlassian
single sign on** to authenticate, make sure to complete the reauthetication
process otherwise Airbrake will not have the access needed for the integration
to work.

# Error 4: Invalid issue type

>400 Bad Request - The issue type selected is invalid.

This error is often the result of your JIRA project not supporting the
**Bug** issue type.
The solution is to [create the **Bug** issue
type](https://confluence.atlassian.com/jira/defining-issue-type-field-values-185729517.html)
for your existing project, or create a new JIRA project that supports the
**Bug** issue type.

# Error 5: Unauthorized

>401 Unauthorized - Please make sure the credentials are correct and try again.

For JIRA standalone, this is often caused by using an email address instead of
your JIRA username in the **username** field. Please verify that you are using
your JIRA username. You can find your JIRA username in your profile page by
clicking your avatar in JIRA.

For JIRA onDemand you should be using **Email** and **API token** instead of
username and password so please make sure you're using the correct email. Also,
please ensure the API token is created on the account with the same email
address as provided in JIRA integration on Airbrake.

### Correct: specifies the username
![jira issues correct username](/docs/assets/img/docs/integrations/jira_issues_correct_username.png)

### Incorrect: specifies the email
![jira issues incorrect username](/docs/assets/img/docs/integrations/jira_issues_incorrect_username.png)

# Error 6: Field is required

>Error: 400 Bad Request - `field_name` is required. Airbrake does not support required field. Please use the default field settings on your Jira account.

This error occurs when your JIRA setup requires a field that Airbrake is not set
up to provide. Please make the field that is mentioned in the error message
optional in your JIRA settings, then test the integration again.

# Error 7: Moved permanently

>Jira integration could not connect. Error: 301 Moved Permanently - Please make sure the credentials are correct and try again.

If you're seeing this error with **onDemand** JIRA but have double checked that
you're using the correct credentials, then please check that you're using
`https` instead of `http` for the **Server URL** field.

# Whitelist IPs

If you're experiencing connection issues please try whitelisting the IPs in the
following doc for your firewall.

[https://airbrake.io/docs/airbrake-faq/what-ips-should-i-whitelist-for-my-firewall/](https://airbrake.io/docs/airbrake-faq/what-ips-should-i-whitelist-for-my-firewall/)
