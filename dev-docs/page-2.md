# Page 2

<figure><img src=".gitbook/assets/02_04_25_add_api_spec.svg" alt="hello world!"><figcaption><p>this is a caption</p></figcaption></figure>

{% tabs %}
{% tab title="iOS" %}
```swift
let context = ContextManager.instantContext(flowName: "upsell_onboarding", duration: 3)
if context.shouldUpsell {
    let vc = MyPremiumOfferViewController()
    vc.userDidPurchase = { product in
        context.logRevenueOutcome(from: product)
    }
    vc.userDidDismiss = {
        context.log(.negative)
    }
    present(vc, animated: true)
} else {
    context.log(.skipped)
}
```
{% endtab %}
{% endtabs %}
