---
description: something something
---

# Page 3

Optimizing conversions begins with tracking them. In ContextDecision, this is done by capturing the user’s context and logging whether a conversion occurred.

Our SDK provides different methods for capturing context, each designed for specific use cases. This document outlines these methods and explains when to use them.

{% hint style="info" %}
If you’re new here, refer to the instructions at [Broken link](broken-reference "mention") for guidance on generating your license key and installing the SDK.
{% endhint %}

## Capturing Context

{% tabs %}
{% tab title="iOS" %}
{% code title="ContextManager.swift" %}
```swift
static func fetchContext(
    flowName: String,
    duration: Int,
    customSignals: [CustomSignal] = [],
    callback: @escaping ((Context) -> Void)
)
```
{% endcode %}
{% endtab %}

{% tab title="Android" %}
{% tabs %}
{% tab title="Kotlin" %}
{% code title="ContextSDK.kt" %}
```kotlin
fun fetchContext(
    flowName: String,
    durationS: Int = 3,
    customSignals: CustomSignals = CustomSignals(),
    callback: (RealWorldContext) -> Unit
)
```
{% endcode %}
{% endtab %}

{% tab title="Java" %}
{% code title="ContextSDK.java" %}
```java
public void fetchContext(
    String flowName,
    int durationS,
    CustomSignals customSignals,
    Consumer<RealWorldContext> callback
)
```
{% endcode %}
{% endtab %}
{% endtabs %}
{% endtab %}

{% tab title="Flutter" %}
{% code title="context_sdk_platform_interface.dart" %}
```dart
Future<int> fetchContext(
  String flowName,
  int duration,
  Map<String, dynamic>? customSignals,
)
```
{% endcode %}
{% endtab %}

{% tab title="Unity" %}
{% code title="ContextSDKBinding.cs" %}
```cs
public static void FetchContext(
    string flowName,
    ContextDelegate callback,
    CustomSignals? customSignals = null,
    int duration = 3
)
```
{% endcode %}
{% endtab %}

{% tab title="React Native" %}
{% code title="index.tsx" %}
```javascript
export function fetchContext(options: {
  flowName: string;
  onContextReady: (context: Context) => void;
  duration?: number;
  customSignals?: CustomSignals;
}): void
```
{% endcode %}
{% endtab %}
{% endtabs %}

This method allows you to capture the user context asynchronously. This is the recommended method to be used in most scenarios.

{% hint style="warning" %}
Always call this method, and other context-capturing methods, **before** displaying an in-app offer. This is because if the context is captured **after** showing the offer, not only ContextDecision can't make a decision on whether to show the offer or not (because it's already been shown), but also the user's context likely will have already changed (e.g. user was lying in bed but once they see an upsell offer they get up or leave the app).
{% endhint %}

When calling this method, you provide:

* A flow name, which uniquely identifies the context being captured. Each flow should have a distinct name, even if the same flow is triggered from different parts of the app. We automatically analyze the overlap between different flows, to decide if there should be one, or more models.
  * **Best practice**: use `snake_case` and group flows that lead to the same prompt using the same prefix, e.g. `upsell_onboarding`, `upsell_first_action` .
* A duration, which determines how long accelerometer and gyroscope data is collected, in seconds. This value must be between 2 and 7 seconds, with a recommended default of 3 seconds.
* An optional array of custom signals, which allows you to append additional contextual information relevant to your flow or app. Learn more in [Broken link](broken-reference "mention").

Once the context is ready, the callback executes asynchronously on the main thread. The execution timing depends on your app’s state:

* If the app has been active and in the foreground for at least 3 seconds (or your configured `duration`), the callback executes instantly.
* If the app was recently launched or resumed from the background, it may take **up to** 3 seconds (or your configured `duration`) for the context to be available.

### Logging Outcomes

An outcome indicates whether an offer led to a conversion (e.g., a purchase, an ad click) or was dismissed. Always log at least one outcome for each captured context to help train the ML models effectively.

For in-app purchases, we require the product that was purchased to be passed as an argument to the outcome log. See [Broken link](broken-reference "mention") for more details.

If your offer is a paywall with a "Restore Purchases" button, see [Broken link](broken-reference "mention").

{% hint style="success" %}
For advanced outcome options, see [Broken link](broken-reference "mention") and [Broken link](broken-reference "mention").
{% endhint %}

### Decision-Making

The `context` object returned by `fetchContext` includes a `shouldUpsell` property, which determines whether an upsell offer should be shown. During the [calibration phase](https://docs.contextsdk.com/other/glossary#calibration-phase), this property always returns `true`. Once a ML model is deployed to the flow, it starts making real-time decisions. If the model determines that it's a bad time, `shouldUpsell` will be `false`, so you can not show the paywall, and thus log `skipped` as the outcome.

{% hint style="info" %}
There are exceptions, such as the [Broken link](broken-reference "mention") use case, where you would show an ad (not a paywall) when `shouldUpsell` is `false`. In these cases, you shouldn't log the `skipped` outcome, but instead log the outcome of your ad interaction.

For more details about this use case, see [Broken link](broken-reference "mention").
{% endhint %}

### Usage Example

To use this method, show the upsell offer inside the callback block to ensure the context is evaluated before presenting the offer. This guarantees that the decision logic runs first, preventing unnecessary offers from being shown when the conditions are not met:

{% tabs %}
{% tab title="iOS" %}
{% code title="MyOnboardingViewController.swift" %}
```swift
// 1. Capture the context
ContextManager.fetchContext(flowName: "upsell_onboarding") { [weak self] context in
    // 2. Check if shouldUpsell is true
    guard context.shouldUpsell else {
        context.log(.skipped) // Log skipped when shouldUpsell is false
        return
    }
    // 3. Create the offer view controller
    let vc = MyPremiumOfferViewController()
    vc.userDidPurchase = { product in
        context.logRevenueOutcome(from: product)
    }
    vc.userDidDismiss = {
        context.log(.negative)
    }
    // 4. Show offer view controller here
    // …
}
```
{% endcode %}
{% endtab %}

{% tab title="Android" %}
{% tabs %}
{% tab title="Kotlin" %}
{% code title="MyOnboardingFragment.kt" %}
```kotlin
// 1. Capture the context
ContextSDK.fetchContext("upsell_onboarding") { context ->
    // 2. Check if shouldUpsell is true
    if (!context.shouldUpsell) {
        context.log(EventOutcome.SKIPPED) // Log skipped when shouldUpsell is false
        return@fetchContext
    }
    // 3. Create the offer fragment
    val fragment = MyPremiumOfferFragment().apply {
        setOnUserDidPurchaseListener { product ->
            context.log(EventOutcome.POSITIVE)
        }
        setOnUserDidDismissListener {
            context.log(EventOutcome.NEGATIVE)
        }
    }
    // 4. Show offer fragment here
    // …
}
```
{% endcode %}
{% endtab %}

{% tab title="Java" %}
{% code title="MyOnboardingFragment.java" %}
```java
// 1. Capture the context
ContextSDK.Companion.fetchContext("upsell_onboarding", null, null, context -> {
    // 2. Check if shouldUpsell is true
    if (!context.getShouldUpsell()) {
        context.log(EventOutcome.SKIPPED); // Log skipped when shouldUpsell is false
        return;
    }
    // 3. Create the offer fragment
    MyPremiumOfferFragment fragment = new MyPremiumOfferFragment();
    fragment.setOnUserDidPurchaseListener(product -> context.log(EventOutcome.POSITIVE));
    fragment.setOnUserDidDismissListener(() -> context.log(EventOutcome.NEGATIVE));
    // 4. Show offer fragment here
    // …
    return Unit.INSTANCE;
});
```
{% endcode %}
{% endtab %}
{% endtabs %}
{% endtab %}

{% tab title="Flutter" %}
{% code title="my_onboarding_screen.dart" %}
```dart
// 1. Capture the context
_contextSdkPlugin.fetchContext("upsell_onboarding", 3).then((context) async {
  // 2. Check if shouldUpsell is true
  if (!(await context.shouldUpsell)) {
      await context.log(Outcome.skipped); // Log skipped when shouldUpsell is false
      return;
  }
  // 3. Create the offer screen
  final offerScreen = PremiumOfferScreen(
    onPurchase: (product) {
      await context.log(Outcome.positive);
    },
    onDismiss: () {
      await context.log(Outcome.negative);
    },
  );
  // 4. Show offer screen here
  // …
});
```
{% endcode %}
{% endtab %}

{% tab title="Unity" %}
{% code title="MyOnboardingScreen.cs" %}
```cs
// 1. Capture the context
ContextSDKBinding.FetchContext("upsell_onboarding", delegate (Context context) {
    // 2. Check if shouldUpsell is true
    if (!context.shouldUpsell) {
        context.Log(Outcome.Skipped); // Log skipped when shouldUpsell is false
        return;
    }
    // 3. Create the offer screen
    var offerScreen = new PremiumOfferScreen();
    offerScreen.OnPurchase = product =>
    {
        context.Log(Outcome.Positive);
    };
    offerScreen.OnDismiss = () =>
    {
        context.Log(Outcome.Negative);
    };
    // 4. Show offer screen here
    // …
});
```
{% endcode %}
{% endtab %}

{% tab title="React Native" %}
{% code title="MyOnboardingScreen.js" %}
```javascript
import { fetchContext, Outcome } from 'react-native-context-sdk';

// 1. Capture the context
fetchContext({
  flowName: 'upsell_onboarding',
  onContextReady: async (context) => {
    // 2. Check if shouldUpsell is true
    if (!(await context.shouldUpsell())) {
        await context.log(Outcome.skipped); // Log skipped when shouldUpsell is false
        return;
    }
    // 3. Create and navigate to the offer screen
    navigation.navigate('PremiumOffer', {
      onPurchase: (product: any) => {
        context.log(Outcome.positive);
      },
      onDismiss: () => {
        context.log(Outcome.negative);
      },
    });
  },
});
```
{% endcode %}
{% endtab %}
{% endtabs %}

If your project does not favor closure-based implementations like shown above when logging outcomes, see [#retrieving-an-existing-context](page-3.md#retrieving-an-existing-context "mention") below for an alternative approach that better fits different architectures.

## Retrieving an Existing Context

Not all architectures use closures for inter-view-controller communication. In such cases, you can capture the context and present the offer in one place, and log the outcome separately. Use the `recentContext(flowName:)` method to retrieve a previously captured context for a given flow name.

{% hint style="info" %}
Note: This method does not capture a new context — it only retrieves an existing one. If no context has been captured for the specified flow, this method returns `nil`.
{% endhint %}

### Usage Example

{% tabs %}
{% tab title="iOS" %}
{% code title="MyOnboardingViewController.swift" %}
```swift
ContextManager.fetchContext(flowName: "upsell_onboarding") { [weak self] context in
    guard context.shouldUpsell else {
        context.log(.skipped)
        return
    }
    self?.present(MyPremiumOfferViewController(), animated: true)
}
```
{% endcode %}

{% code title="MyPremiumOfferViewController.swift" %}
```swift
func userDidCompletePurchase(product: Product) {
    if let context = ContextManager.recentContext(flowName: "upsell_onboarding") {
        context.logRevenueOutcome(from: product)
    } else {
        // This is an error state. Make sure the context above is created first.
    }
}

func dismissViewController() {
    if let context = ContextManager.recentContext(flowName: "upsell_onboarding") {
        context.log(.negative)
    } else {
        // This is an error state. Make sure the context above is created first.
    }
    // Dismiss your view controller here
}
```
{% endcode %}
{% endtab %}

{% tab title="Android" %}
{% tabs %}
{% tab title="Kotlin" %}
{% code title="MyOnboardingFragment.kt" %}
```kotlin
ContextSDK.fetchContext("upsell_onboarding") { context ->
    if (!context.shouldUpsell) {
        context.log(EventOutcome.SKIPPED)
        return@fetchContext
    }
    val fragment = MyPremiumOfferFragment()
    // Show fragment here
}
```
{% endcode %}

{% code title="MyPremiumOfferFragment.kt" %}
```kotlin
fun userDidCompletePurchase(product: Product) {
    val context = ContextSDK.recentContext("upsell_onboarding")
    if (context != null) {
        context.log(EventOutcome.POSITIVE)
    } else {
        // This is an error state. Make sure the context above is created first.
    }
}

fun dismissFragment(fragment: Fragment) {
    val context = ContextSDK.recentContext("upsell_onboarding")
    if (context != null) {
        context.log(EventOutcome.NEGATIVE)
    } else {
        // This is an error state. Make sure the context above is created first.
    }
    // Dismiss the fragment here
}
```
{% endcode %}
{% endtab %}

{% tab title="Java" %}
{% code title="MyOnboardingFragment.java" %}
```java
ContextSDK.Companion.fetchContext("upsell_onboarding", null, null, context -> {
    if (!context.getShouldUpsell()) {
        context.log(EventOutcome.SKIPPED);
        return;
    }
    MyPremiumOfferFragment fragment = new MyPremiumOfferFragment();
    // Show fragment here
    return Unit.INSTANCE;
});
```
{% endcode %}

{% code title="MyPremiumOfferFragment.java" %}
```java
public void userDidCompletePurchase(Product product) {
    RealWorldContext context = ContextSDK.Companion.recentContext("upsell_onboarding");
    if (context != null) {
        context.log(EventOutcome.POSITIVE);
    } else {
        // This is an error state. Make sure the context above is created first.
    }
}

public void dismissFragment(Fragment fragment) {
    RealWorldContext context = ContextSDK.Companion.recentContext("upsell_onboarding");
    if (context != null) {
        context.log(EventOutcome.NEGATIVE);
    } else {
        // This is an error state. Make sure the context above is created first.
    }
    // Dismiss the fragment here
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
{% endtab %}

{% tab title="Flutter" %}
{% code title="my_onboarding_screen.dart" %}
```dart
_contextSdkPlugin.fetchContext("upsell_onboarding", 3).then((context) async {
  if (!(await context.shouldUpsell)) {
      await context.log(Outcome.skipped);
      return;
  }
  // Show offer screen here
  // …
});
```
{% endcode %}

{% code title="my_premium_offer_screen.dart" %}
```dart
void userDidCompletePurchase(Product product) async {
  final context = await _contextSdkPlugin.recentContext("upsell_onboarding");
  if (context != null) {
    await context.log(Outcome.positive);
  } else {
    // This is an error state. Make sure the context above is created first.
  }
}

void dismissView(BuildContext context) async {
  final context = await _contextSdkPlugin.recentContext("upsell_onboarding");
  if (context != null) {
    await context.log(Outcome.negative);
  } else {
    // This is an error state. Make sure the context above is created first.
  }
  // Dismiss screen here
}
```
{% endcode %}
{% endtab %}

{% tab title="Unity" %}
{% code title="MyOnboardingScreen.cs" %}
````cs
// 1. Capture the context
ContextSDKBinding.FetchContext("upsell_onboarding", delegate (Context context) {
    // 2. Check if shouldUpsell is true
    if (!context.shouldUpsell) {
        context.Log(Outcome.Skipped);
        return;
    }
    // 3. Show offer screen here
    // …
});

</div>

<div data-gb-custom-block data-tag="code" data-title='MyPremiumOfferScreen.cs'>

```cs
public void UserDidCompletePurchase(Product product)
{
    var context = ContextSDKBinding.RecentContext("upsell_onboarding");
    if (context != null)
    {
        context.Log(Outcome.Positive);
    }
    else
    {
        // This is an error state. Make sure the context above is created first.
    }
}

public void DismissView()
{
    var context = ContextSDKBinding.RecentContext("upsell_onboarding");
    if (context != null)
    {
        context.Log(Outcome.Negative);
    }
    else
    {
        // This is an error state. Make sure the context above is created first.
    }

    // Dismiss screen here
}
````
{% endcode %}
{% endtab %}

{% tab title="React Native" %}
{% code title="MyOnboardingScreen.js" %}
```javascript
import { fetchContext, Outcome } from 'react-native-context-sdk';

fetchContext({
  flowName: 'upsell_onboarding',
  onContextReady: async (context) => {
    if (!(await context.shouldUpsell())) {
        await context.log(Outcome.skipped);
        return;
    }
    navigation.navigate('PremiumOffer');
  },
});
```
{% endcode %}

{% code title="MyPremiumOfferScreen.js" %}
```javascript
import { recentContext, Outcome } from 'react-native-context-sdk';

const userDidCompletePurchase = async (product) => {
  const context = await recentContext("upsell_onboarding");
  if (context) {
    await context.log(Outcome.positive);
  } else {
    // This is an error state. Make sure the context above is created first.
  }
};

const dismissScreen = async (navigation) => {
  const context = await recentContext("upsell_onboarding");
  if (context) {
    await context.log(Outcome.negative);
  } else {
    // This is an error state. Make sure the context above is created first.
  }
  // Dismiss your screen here
};
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Advanced

### Canceling a Pending Context Callback

The `cancelContextCallback(flowName:)` method allows you to cancel a pending context evaluation for a specific flow. Use this method if you have previously called one of the asynchronous methods above but no longer need the resulting context.

This is particularly useful in cases where the user navigates away from the screen before the context evaluation completes. Since context capturing is asynchronous, the callback may be executed at a later time, potentially in an unintended screen or state. Calling `cancelContextCallback(flowName:)` prevents this from happening by discarding the pending callback if it hasn’t already been triggered.

#### Usage Example

If you use context evaluation to decide whether to display an upsell offer, but the user leaves the screen before the prompt appears, you can call:

{% tabs %}
{% tab title="iOS" %}
```swift
ContextManager.cancelContextCallback(for: "upsell")
```
{% endtab %}

{% tab title="Android" %}
{% tabs %}
{% tab title="Kotlin" %}
Not yet supported in Android. Reach out to our team to request this feature.
{% endtab %}

{% tab title="Java" %}
Not yet supported in Android. Reach out to our team to request this feature.
{% endtab %}
{% endtabs %}
{% endtab %}

{% tab title="Flutter" %}
Not yet supported in Flutter. Reach out to our team to request this feature.
{% endtab %}

{% tab title="Unity" %}
Not yet supported in Unity. Reach out to our team to request this feature.
{% endtab %}

{% tab title="React Native" %}
Not yet supported in React Native. Reach out to our team to request this feature.
{% endtab %}
{% endtabs %}

This ensures the upsell offer is never shown, which helps maintain a seamless user experience by preventing outdated context-based actions from executing at inappropriate times.

### Capturing an Instant Context

Use the `instantContext(flowName:)` method when context must be captured immediately, with no tolerance for delays:

{% tabs %}
{% tab title="iOS" %}
{% code title="ContextManager.swift" %}
```swift
@discardableResult
static func instantContext(
    flowName: String,
    duration: Int,
    customSignals: [CustomSignal] = []
) -> Context
```
{% endcode %}
{% endtab %}

{% tab title="Android" %}
{% tabs %}
{% tab title="Kotlin" %}
{% code title="ContextSDK.kt" %}
```kotlin
fun instantContext(
    flowName: String,
    durationS: Int = 3,
    customSignals: CustomSignals = CustomSignals(),
): RealWorldContext
```
{% endcode %}
{% endtab %}

{% tab title="Java" %}
{% code title="ContextSDK.java" %}
```java
public RealWorldContext instantContext(
    String flowName,
    int durationS,
    CustomSignals customSignals
)
```
{% endcode %}
{% endtab %}
{% endtabs %}
{% endtab %}

{% tab title="Flutter" %}
{% code title="context_sdk_platform_interface.dart" %}
```dart
Future<int> instantContext(
  String flowName,
  int duration,
  Map<String, dynamic>? customSignals,
)
```
{% endcode %}
{% endtab %}

{% tab title="Unity" %}
{% code title="ContextSDKBinding.cs" %}
```csharp
public static Context InstantContext(
    string flowName,
    CustomSignals? customSignals = null,
    int duration = 3
)
```
{% endcode %}
{% endtab %}

{% tab title="React Native" %}
{% code title="index.tsx" %}
```javascript
export async function instantContext(options: {
  flowName: string;
  duration?: number;
  customSignals?: CustomSignals;
}): Promise<Context>
```
{% endcode %}
{% endtab %}
{% endtabs %}

This method is ideal for user-initiated triggers, such as:

* Determining whether to display an upsell offer when the user presses a button to navigate to the next screen.
* Capturing context when the user presses a button to show the subscription flow. This can be useful to provide additional data for ML models.

In those cases, waiting up to 3 seconds is not an option, as it would seem like the app became unresponsive (at least if done without showing a loader).

The down side of this method is that if the app hasn't been in the foreground for at least 3 seconds, the quality of the signals captured may be poor and thus unsuitable for ML training. Thus, if this method needs to be used, keep in mind that it might end up taking longer to capture quality data to train your models.

#### Usage Example
