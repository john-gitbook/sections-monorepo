---
description: >-
  This page describes how to use the AWS Cognito integration to publish your
  site behind Visitor Authentication
---

# How to use the AWS Cognito Integration for Visitor Authentication

## Installing the Cognito integration

Navigate to integrations within the GitBook app, select Visitor Authentication as the category, and install the AWS Cognito integration.

<figure><img src="../../../.gitbook/assets/Screen Shot 2024-12-13 at 3.37.39 PM.png" alt=""><figcaption></figcaption></figure>



Once you've installed it on your site, go to configuration and make a note of the Callback URL right above the Save button. We will need it to set up Cognito.&#x20;

## Setting up Cognito

Go to your desired User Pool in Cognito, and click on App integration. Make a note of the Cognito domain, we will need it to configure the integration.

Scroll to the bottom and click "Create app client". For the app type, select "Confidential client." Scroll down to Hosted UI settings. In allowed Callback URLs, enter the Callback URL you got from GitBook upon installing the integration on a space.

Scroll further down to "OAuth 2.0 grant types"- make sure "Authorization code grant" is selected.

For "OpenID connect scopes", make sure OpenID is selected.

Scroll down and click "Create app client".

Click on the created app client and make a note of the Client ID and Client Secret.

## Configuring the integration

Open up the Cognito integration's configuration screen for the space you installed the integration on.

It should look like the following image:

<figure><img src="../../../.gitbook/assets/Screen Shot 2024-12-13 at 3.41.57 PM.png" alt=""><figcaption></figcaption></figure>

For Client ID, Cognito Domain, and Client Secret, paste in the values you got from Cognito.

Hit Save.

Now, in GitBook, close the integrations modal and click on the Manage site button. Navigate to Audience, select Visitor Authentication, and choose Cognito as the backend. and click Update audience. Go to the site's screen and click Publish.\
\
The site is now published behind Visitor Authentication controlled by your Cognito application. To try it out, click on Visit. You will be asked to sign in with Cognito, which confirms that your site is published behind Visitor Authentication using AWS Cognito.
