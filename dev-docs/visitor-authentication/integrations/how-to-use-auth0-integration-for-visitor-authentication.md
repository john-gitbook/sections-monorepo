---
description: >-
  This page describes how to use the Auth0 integration to publish your site
  behind Visitor Authentication
---

# How to use Auth0 Integration for Visitor Authentication

## Setting up Auth0

First, sign in to Auth0 platform and create a new application (or use an existing one) by clicking the Applications button in the left sidebar. If creating a new application, name it appropriately and choose "Regular Web Application" as the option. Click Create. You may need to be admin to follow along this guide.\


<figure><img src="../../.gitbook/assets/Screen Shot 2023-10-25 at 4.52.25 PM.png" alt=""><figcaption></figcaption></figure>

A quickstart panel will show up. Select Node.js (Express) option and then select "I want to integrate my app."  You will see a screen prompting you to configure Auth0. It should look like the image below

<figure><img src="../../.gitbook/assets/Screen Shot 2023-10-25 at 4.54.42 PM.png" alt=""><figcaption></figcaption></figure>

Click on Save Settings And Continue.

Click on Settings next to Quickstart, and make a note of the Domain, Client ID, and Client Secret.\
\
We will need these to configure our Auth0 Visitor Authentication Integration.

{% hint style="info" %}
Please ensure at least one connection is enabled for your Auth0 application.
{% endhint %}

<figure><img src="../../.gitbook/assets/Screen Shot 2024-05-28 at 5.00.39 PM.png" alt=""><figcaption></figcaption></figure>

## Installing the Auth0 Visitor Authentication Integration

\
Navigate to the Integrations tab in a site and locate the Auth0 integration or navigate directly to this [https://app.gitbook.com/integrations/VA-Auth0](https://app.gitbook.com/integrations/VA-Auth0).

<figure><img src="broken-reference" alt=""><figcaption></figcaption></figure>

Install the integration on your site.



Upon installation on site, you will see a modal asking you enter the Client ID, Auth0 Domain, and Client Secret.

<figure><img src="broken-reference" alt=""><figcaption></figcaption></figure>

For Client ID and Client Secret, paste in the value you copied from Auth0 Dashboard. For Auth0 Domain, enter the Domain copied from Auth0 (make sure to prefix it with `https://`) .

Click Save.

Copy the URL displayed in the modal and enter it as an Allowed Callback URL in Auth0 (shown in the second screenshot in this guide). Hit Save

Now, in GitBook, close the integrations modal and click on the Manage site button. Navigate to Audience, select Visitor Authentication, and choose Auth0 as the backend. and click Update audience. Go to the site's screen and click Publish.\
\
The site is now published behind Visitor Authentication controlled by your Auth0 application. To try it out, click on Visit. You will be asked to sign in with Auth0, which confirms that your site is published behind Visitor Authentication using Auth0.
