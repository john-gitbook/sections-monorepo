---
description: >-
  Get started developing in GitBook by setting up the GitBook CLI in your local
  environment.
icon: rectangle-terminal
---

# Quickstart

{% stepper %}
{% step %}
### Install the GitBook CLI

The GitBook Development CLI requires Node v18 or later. It can be installed from NPM using:

```
npm install @gitbook/cli -g
```
{% endstep %}

{% step %}
### Authenticate with your account

Create an API token in your GitBook.com at [app.gitbook.com/account/developer](https://app.gitbook.com/account/developer).

Then run the following command to authenticate locally:

```
gitbook auth
```
{% endstep %}

{% step %}
### Bootstrap your app

Bootstrap your first app by running:

```
gitbook new
```
{% endstep %}
{% endstepper %}
