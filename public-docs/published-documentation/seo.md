---
description: Optimize your GitBook documentation to be discoverable via search engines.
icon: print-magnifying-glass
---

# SEO

Thanks to the following features, your GitBook projects are SEO-friendly with little or no configuration on your end:

<details>

<summary>Responsive design</summary>

All content is suitable for mobile devices, tablets, laptops and desktops! The design for your published documentation will adapt based on the size of the device it is being viewed on.

</details>

<details>

<summary>SEO-friendly content</summary>

* URLs are set based on each page’s title by default, but can be customized as you wish.
* We avoid duplicate content through smart, canonical URLs.
* The HTML title and Open Graph title are based on the page and space title.
* The meta description and Open Graph description are based on the page description.
* Alt text can be added to images, which is also very important for accessibility.
* HTML sent to crawlers is pre-rendered (i.e. server-side), meaning that crawlers do not need JavaScript to index your content.

Note that we _don’t_ generate keyword meta tags, because modern search engines do not use them to rank pages. This was [officially confirmed by Google](https://developers.google.com/search/blog/2009/09/google-does-not-use-keywords-meta-tag) in 2009.

</details>

<details>

<summary>Sitemap</summary>

Provided that your space is published with a setting _other_ than [unlisted](../collaboration/share/share-a-space.md#unlisted-space), we automatically generate a sitemap.xml file based on your [table of contents](https://docs.gitbook.com/getting-started/overview#table-of-contents). You can locate this by going to the first page of your documentation and then appending `/sitemap.xml` to the URL. For example, the first page of our documentation is located at [docs.gitbook.com](https://docs.gitbook.com/), and so our sitemap.xml file is located at [docs.gitbook.com/sitemap.xml](https://docs.gitbook.com/sitemap.xml).

</details>

<details>

<summary>Custom domain</summary>

If you prefer, you can [set a custom domain](custom-domain/) for your documentation. (e.g. `docs.example.com` instead of `yourorganization.gitbook.io`)

</details>

<details>

<summary>Caching &#x26; CDN</summary>

All published content is cached and served via our global CDN (content delivery network). This helps to improve performance, which is an important factor within SEO.

</details>

Even with these great features, it could still take some time before your documentation is indexed by Google (and other search engines). Both we and you have no _direct_ control over this, but there are two things that you could do to help improve the chance of getting your content indexed more quickly:

1. Make sure that there are links to your GitBook space from other websites that have already been indexed by Google. As Google will return to re-index these sites from time to time, this increases the chance that they’ll find your space as a result of re-indexing one of these other sites.
2. Try [submitting your site to Google](https://developers.google.com/search/docs/advanced/crawling/ask-google-to-recrawl), which essentially asks them to index it. For GitBook spaces, this will only be possible if you are using a [custom domain](custom-domain/) for your space _and_ if you create a TXT DNS record to confirm ownership of the domain.

### Redirects

Moving your content to GitBook or changing its structure? Broken links can impact your SEO. [Read how to set up redirects in GitBook](site-redirects.md).

{% hint style="info" %}
**Note:** Whenever you move or rename a page within GitBook, its canonical URL also changes. To keep your content accessible, GitBook automatically creates a [HTTP 301](https://en.wikipedia.org/wiki/HTTP_301) redirect from the old URL to the new one. Find out more about how automatic redirects work on [our redirects page](site-redirects.md#about-automatic-redirects).
{% endhint %}
