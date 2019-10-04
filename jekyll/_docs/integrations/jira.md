---
layout: classic-docs
title: JIRA
categories: [integrations]
description: JIRA
---


Tired of wasting your limited time scraping together the context and
details needed to create useful JIRA issues? By the end of this doc Airbrake
will be automatically creating them for you!

When your Airbrake project receives a new error a corresponding
[JIRA](http://www.atlassian.com/software/jira/overview) issue is created.
JIRA issues created by Airbrake let you get to work quickly on
problems effecting your users, giving you everything you need to solve problems
fast!

This integration supports **onDemand** and **Standalone** versions of JIRA.

## Configuring the JIRA integration

1. Click **Integrations** for your project
2. Click **JIRA**

Identify which type of JIRA setup you are using. **OnDemand** means you're using an
Atlassian account. **Standalone** means you setup JIRA yourself or with a 3rd
party.

### JIRA onDemand integration:

![jira-ondemand-settings](/docs/assets/img/docs/integrations/jira-ondemand-settings.png)

### JIRA onDemand settings:
- Server URL: http://myaccount.atlassian.net
- Email: your-jira@email.com
- API token: your-api-token
- Project key: EXAMPLE

**Please ensure the API token is created on the account with the same email
address as provided in JIRA integration on Airbrake.** You can create a new API
token [here](https://id.atlassian.com/manage/api-tokens).

### JIRA standalone integration:

![jira-standalone-settings](/docs/assets/img/docs/integrations/jira-standalone-settings.png)

### JIRA standalone settings:
- Server URL: http://jiraurl.mywebsite.com
- Context Path: /jira
- Username: Jirauser
- Password: JirauserPass
- Project key: EXAMPLE

**Please ensure the user you provide has proper permissions to the Project.**

## Testing your JIRA integration settings

Testing your JIRA integration settings is as easy as clicking on the **Test
integration** link found at the bottom of the window after setup is complete.

![jira test link](/docs/assets/img/docs/integrations/jira_testing.png)

You should see notification about integration success.
If the test reports any issues, please check our doc on [troubleshooting jira issues](/docs/integrations/troubleshooting-jira-issues).

## Manually create a JIRA issue from an Airbrake error

Select the error you want to create a JIRA issue for, in the errors overview
tab, click the **Create JIRA Issue** button:

![jira button](/docs/assets/img/docs/integrations/jira_button.png)

After the JIRA issue is created your Airbrake error will show a link to go the
JIRA issue. The JIRA issue will also link back to get back to the Airbrake error.
If you would like to remove the association between the Error and issue, just
click the **Remove** button:

![jira issue link](/docs/assets/img/docs/integrations/jira_issue_link.png)

## Integrating with a next-gen JIRA project

If you're integrating with a next-gen JIRA project, please make sure to disable
the **'Include separate "environment" field when creating issues'** option because
next-gen JIRA projects do not have an "environment" field available.

![jira env field](/docs/assets/img/docs/integrations/jira_include_environment_field.png)
