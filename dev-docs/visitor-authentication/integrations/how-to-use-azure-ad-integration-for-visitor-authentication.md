---
description: >-
  This page describes how to use the Azure AD  (now known as Microsoft Entra ID)
  integration to publish your site behind Visitor Authentication
---

# How to use Azure AD Integration for Visitor Authentication

{% hint style="info" %}
There is a known limitation with the Azure integration where heading URL fragments will be removed upon authentication. The user will still land on the correct page, but will be taken to the top of the page instead of the heading in the URL. Once an user is authenticated this behavior will no longer occur during a session and the user would be directed to the correct heading.

This is due to a security measure put in place by Microsoft.
{% endhint %}

## Setting up Entra

First, sign in to Entra platform. In the left sidebar, navigate to Identity > Applications > App registrations. You may need admin permissions to do this.\


<figure><img src="../../../.gitbook/assets/Screen Shot 2023-11-02 at 3.58.44 PM.png" alt=""><figcaption></figcaption></figure>

And click on New registration button in the screen that opens up. Name it appropriately.

Under **Supported account types,** select **Accounts in this organizational directory only.**

Click Register.

You should see a screen like the following

<figure><img src="../../../.gitbook/assets/Screen Shot 2023-11-02 at 4.18.19 PM.png" alt=""><figcaption></figcaption></figure>



Go back to the Overview page. Make a note of the Application (client) ID and Directory (tenant) ID.

<figure><img src="../../../.gitbook/assets/Screen Shot 2023-11-02 at 4.18.19 PM.png" alt=""><figcaption></figcaption></figure>

Click on "Add a certificate or secret". You should see the following screen

<figure><img src="../../../.gitbook/assets/Screen Shot 2023-11-02 at 5.25.41 PM.png" alt=""><figcaption></figcaption></figure>

Click on "New client secret". Enter a suitable description in the side panel that shows up and click add. Copy the **value** of the secret (not Secret ID) just created. This would be the Client Secret.\


We will need these to configure our Azure Visitor Authentication Integration.

## Installing the Azure Visitor Authentication Integration

\
Navigate to the Integrations tab in a site and locate the Azure integration or navigate directly to this [https://app.gitbook.com/integrations/VA-Azure](https://app.gitbook.com/o/d8f63b60-89ae-11e7-8574-5927d48c4877/s/zq8ynchcecIscc4uulgN/).

<figure><img src="broken-reference" alt=""><figcaption></figcaption></figure>

Install the integration on your site.

Upon installation on site, you will see a screen asking you enter the Client ID, Tenant ID, and Client Secret.

<figure><img src="broken-reference" alt=""><figcaption></figcaption></figure>



For Client ID, Tenant ID, and Client Secret, paste in the value you copied from Entra Dashboard.&#x20;

Click Save.

Copy the URL displayed in the modal and enter it as a Redirect URI in Entra (as shown in the below screenshot). Hit Save. Note that you may need to select Web as a platform before it lets you enter a Redirect URI.

<figure><img src="../../../.gitbook/assets/Screen Shot 2024-01-14 at 6.51.07 PM.png" alt=""><figcaption></figcaption></figure>

Now, in GitBook, close the integrations modal and click on the Manage site button. Navigate to Audience, select Visitor Authentication, and choose Azure as the backend. and click Update audience. Go to the site's screen and click Publish.\
\
The site is now published behind Visitor Authentication controlled by your Azure application. To try it out, click on Visit. You will be asked to sign in with Azure, which confirms that your site is published behind Visitor Authentication using Azure.



{% hint style="info" %}
Upon accessing the published content URL and after logging in with your Azure credentials, you may see a screen telling you that you need to "Request approval" from your admin. Your admin can grant this request by accessing the published content URL, logging in, and granting approval on behalf of the organization.
{% endhint %}

