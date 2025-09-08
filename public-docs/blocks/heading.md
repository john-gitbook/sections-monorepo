---
description: Add heading blocks to a page to organize your content and improve SEO.
---

# Headings

Headings help give your documents structure — and using keywords in headings will also help search engines understand that structure, which can help your page rank higher in search results.

GitBook offers three levels of headings. Heading levels 1 (H1) and 2 (H2) will appear in the [page outline](../editor/navigation.md#page-outline).

{% hint style="info" %}
Reading on a screen is less comfortable than reading on paper. Sometimes splitting longer content into different [pages](../editor/content-structure/content-in-a-space.md) can help with overall readability.
{% endhint %}

### Anchor links

When you add a heading to a page, it creates an anchor link. You can then link directly to these specific sections, to point people to relevant information.

#### Link to an anchor

You can see anchor links in public content, or private content in read-only mode, by hovering over the title and clicking the `#` that appears next to it. This will update the URL in your browser’s top bar, so you can copy it to use elsewhere.

If you want to link to a particular anchor from a page within your GitBook space, you can use a [relative link](../editing-content/inline.md#relative-links), which will update if you change the heading to prevent the link from breaking.

#### Edit an anchor

By default, the anchor link will be identical to the text in your header. If you plan to link to that URL outside of GitBook, changing the header in future will break the anchor link. The link will then take visitors to the top of the page, rather than the anchor location.

To avoid this, you can manually set the anchor link by opening the **Options menu** <img src="../../.gitbook/assets/Options menu.png" alt="" data-size="line"> for the header, then choosing **Edit anchor**. You can then enter the anchor link you wish to use — this will remain the anchor even if you change the header itself.

### Heading examples <a href="#example-of-a-heading" id="example-of-a-heading"></a>

## My heading 1

### My heading 2

#### My heading 3

### Representation in Markdown

{% code overflow="wrap" %}
```markdown
# My heading 1
## My heading 2
### My heading 3
```
{% endcode %}
