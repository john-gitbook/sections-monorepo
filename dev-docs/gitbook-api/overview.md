---
description: >-
  Leverage the power of GitBook's API to create powerful integrations with your
  favorite tools and services.
icon: bullseye-arrow
---

# Overview

The GitBook API allows you to read and write information across the spaces and pages you have access to in GitBook. You can do things like update permissions for members in an organization, create change requests, and much more.

This section describes how to use the GitBook API and its resources. If you have any questions or issues, please contact the [GitBook Support](mailto:support@gitbook.com).

[#discover-the-platform](../#discover-the-platform "mention")

[#company-information](../getting-started/setup-guide.md#company-information "mention")

[Discover the platform](https://app.gitbook.com/s/DmprpEOqauZ42zPVKuae/getting-started/readme#discover-the-platform "mention")

[Example](https://app.gitbook.com/s/DmprpEOqauZ42zPVKuae/gitbook-api/pagination#example "mention")

{% content-ref url="https://app.gitbook.com/s/DmprpEOqauZ42zPVKuae/getting-started" %}
[Getting Started](https://app.gitbook.com/s/DmprpEOqauZ42zPVKuae/getting-started)
{% endcontent-ref %}

### API Endpoint

The GitBook API can be accessed using the `api.gitbook.com` hostname:

```bash
curl https://api.gitbook.com/v1/
{"version":"10.9.128","build":"2022-07-19T13:00:05.548Z"}
```

### API Reference

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-cover data-type="files"></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>API Reference</strong></td><td>Learn more about the endpoints you can use from GitBook's REST API</td><td><a href="../.gitbook/assets/GitBook API.svg">GitBook API.svg</a></td><td><a href="reference/">reference</a></td></tr><tr><td><strong>API Explorer</strong></td><td>Try out the GitBook API and view responses</td><td><a href="../.gitbook/assets/API Explorer.svg">API Explorer.svg</a></td><td><a href="https://api-explorer.gitbook.dev/">https://api-explorer.gitbook.dev/</a></td></tr></tbody></table>

### Authentication & Rate Limiting

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td><strong>Authentication</strong></td><td>Create an API access token and authenticate your API requests.</td><td><a href="authentication.md">authentication.md</a></td><td><a href="../.gitbook/assets/Authentication.svg">Authentication.svg</a></td></tr><tr><td><strong>Rate Limiting</strong></td><td>Understand how API requests are rate limited.</td><td><a href="rate-limiting.md">rate-limiting.md</a></td><td><a href="../.gitbook/assets/Rate Limiting.svg">Rate Limiting.svg</a></td></tr></tbody></table>

### Errors & Pagination

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td><strong>Errors</strong></td><td>Learn about API errors, how they're structured and how to handle them.</td><td><a href="errors.md">errors.md</a></td><td><a href="../.gitbook/assets/Errors.svg">Errors.svg</a></td></tr><tr><td><strong>Pagination</strong></td><td>Paginate through API List results.</td><td><a href="pagination.md">pagination.md</a></td><td><a href="../.gitbook/assets/Pagination.svg">Pagination.svg</a></td></tr></tbody></table>

### Client Libraries

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td><strong>Libraries</strong></td><td>Use our libraries to interact with the API.</td><td><a href="librairies/">librairies</a></td><td><a href="../.gitbook/assets/Node.js.svg">Node.js.svg</a></td></tr></tbody></table>

### Changelog & Feedback

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td><strong>API Changelog</strong></td><td>Read about what changed with the API.</td><td><a href="https://github.com/GitbookIO/integrations/releases">https://github.com/GitbookIO/integrations/releases</a></td><td><a href="../.gitbook/assets/Changelog.svg">Changelog.svg</a></td></tr><tr><td><strong>Support</strong></td><td>Share your feedback to improve the API and ensure it fits your needs.</td><td><a href="broken-reference">Broken link</a></td><td><a href="../.gitbook/assets/Support.svg">Support.svg</a></td></tr></tbody></table>
