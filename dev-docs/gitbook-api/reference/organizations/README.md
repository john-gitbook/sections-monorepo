---
description: >-
  An organization in GitBook is the entity of a place that users, spaces, and
  collections belong to.
---

# Organizations

<figure><img src="../../../.gitbook/assets/Organization.png" alt=""><figcaption></figcaption></figure>

{% openapi src="https://api.gitbook.com/openapi.json" path="/orgs" method="get" expanded="true" %}
[https://api.gitbook.com/openapi.json](https://api.gitbook.com/openapi.json)
{% endopenapi %}

{% openapi src="https://api.gitbook.com/openapi.json" path="/orgs/{organizationId}/collections" method="get" expanded="true" %}
[https://api.gitbook.com/openapi.json](https://api.gitbook.com/openapi.json)
{% endopenapi %}

{% openapi src="https://api.gitbook.com/openapi.json" path="/orgs/{organizationId}/spaces" method="get" expanded="true" %}
[https://api.gitbook.com/openapi.json](https://api.gitbook.com/openapi.json)
{% endopenapi %}

{% openapi src="https://api.gitbook.com/openapi.json" path="/orgs/{organizationId}/spaces/gitsync" method="get" %}
[https://api.gitbook.com/openapi.json](https://api.gitbook.com/openapi.json)
{% endopenapi %}
