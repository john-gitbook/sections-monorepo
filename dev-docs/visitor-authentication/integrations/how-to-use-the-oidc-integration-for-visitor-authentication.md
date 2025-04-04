---
description: >-
  This page describes how to use the OIDC integration to publish your site
  behind Visitor Authentication
---

# How to use the OIDC Integration for Visitor Authentication

## Introduction

OIDC stands for OpenID Connect, and it's an identity layer built on top of OAuth. Many identity providers abide by OIDC, and GitBook's OIDC integration for Visitor Authentication allows you to publish your space behind Visitor Authentication, and access to the content is controlled by your Identity Provider

{% hint style="info" %}
Since this guide is a generic guide meant for all identity providers, some details may vary depending on your Identity Provider. For illustration purposes, we are using Google as the identity provider in this guide.
{% endhint %}

## Installing the OIDC integration

Navigate to integrations within the GitBook app, select Visitor Authentication as the category, and install the OIDC integration. Install the OIDC integration on your chosen docs site.

<figure><img src="../../.gitbook/assets/Screen Shot 2024-12-13 at 3.37.39 PM.png" alt=""><figcaption></figcaption></figure>

Once you've installed it on your site, go to configuration and make a note of the Callback URL right above the Save button. We may need it to set up the Identity Provider.&#x20;

## Setting up your Identity Provider

{% hint style="info" %}
Note that the exact terminology and steps may vary depending on your Identity Provider. We are using Google in this guide for illustration purposes
{% endhint %}

There are some things that you need to set up on your Identity Provider in order to get the integration to work.

You need to create a new app inside your Identity Provider. Its type should be "Web Application." In Google, you create these under "API and Services", "Credentials", and then under "OAuth 2.0 Client IDs."\


<figure><img src="../../.gitbook/assets/Screen Shot 2024-05-15 at 11.19.59 AM.png" alt=""><figcaption></figcaption></figure>

Click on Create Credentials, select OAuth Client ID, select Web Application as the type, name it appropriately, and under Authorized Redirect URIs, enter the Callback URL you got from GitBook.

Click Create. Make a note of the Client ID and Client Secret. We will need these to finish configuring of our integration in GitBook.

## Configuring the integration

Open up the OIDC integration's configuration screen for the space you installed the integration on.

It should look like the following image

<figure><img src="../../.gitbook/assets/Screen Shot 2024-12-13 at 3.38.30 PM.png" alt=""><figcaption></figcaption></figure>



For Client ID and Client Secret, paste in the values you got for your identity provider.

Now, you will need to find the Authorization Endpoint and Access Token Endpoint for your Identity Provider. For Google, these are `https://accounts.google.com/o/oauth2/v2/auth` and `https://oauth2.googleapis.com/token` respectively.&#x20;

{% hint style="info" %}
If you are not using Google, these endpoints will be different for you. Please look into the documentation of your identity provider to locate these endpoints
{% endhint %}

For OAuth Scope, its value will be again be different depending on your Identity Provider. In case of Google, you can enter `openid`.

{% hint style="info" %}
Please look at the list of allowed scopes in your Identity Provider's documentation, and enter the value of the least permissive scope. We only use the Access Token to verify that the user is authenticated, and we do not use the Access Token to fetch any further information. So, entering the least permissive scope is the best security recommendation.
{% endhint %}

Hit Save.

Now, in GitBook, close the integrations modal and click on the Manage site button. Navigate to Audience, select Visitor Authentication, and choose OIDC as the backend. and click Update audience. Go to the site's screen and click Publish.\
\
The site is now published behind Visitor Authentication controlled by your OIDC application. To try it out, click on Visit. You will be asked to sign in with your OIDC provider, which confirms that your site is published behind Visitor Authentication using OIDC provider.
