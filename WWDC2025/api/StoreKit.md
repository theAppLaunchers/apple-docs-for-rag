Framework

# StoreKit

Support In-App Purchases and interactions with the App Store.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.0+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 6.2+

## [Overview](/documentation/StoreKit#overview)

Use the StoreKit framework to provide the following features and services for your apps and In-App Purchases:

In-App Purchase

Offer and promote In-App Purchases for content and services.

App transaction

Verify a customer’s app purchase with an App Store-signed transaction.

Messages

Control the display of App Store messages in your app.

Reviews

Request App Store reviews and ratings from your customers.

Recommendations

Provide recommendations for third-party content that customers can purchase from the App Store.

Ad network attribution

Validate advertisement-driven app installations. See [AdAttributionKit](/documentation/AdAttributionKit) for app ad campaigns on the App Store and alternative marketplaces.

The StoreKit framework also provides functionality for [External Purchase](/documentation/storekit/external-purchase), [External link account](/documentation/storekit/external-link-account), [`PaymentMethodBinding`](/documentation/storekit/paymentmethodbinding), and [`StoreDownloaderExtension`](/documentation/storekit/storedownloaderextension).

## [Topics](/documentation/StoreKit#topics)

### [In-App Purchase](/documentation/StoreKit#In-App-Purchase)

[

API Reference

In-App Purchase](/documentation/storekit/in-app-purchase)

Offer content and services in your app across Apple platforms using a Swift-based interface.

[

Understanding StoreKit workflows](/documentation/storekit/understanding-storekit-workflows)

Implement an in-app store with several product types, using StoreKit views.

[

Getting started with In-App Purchase using StoreKit views](/documentation/storekit/getting-started-with-in-app-purchases-using-storekit-views)

Set up an in-app store using SwiftUI and StoreKit views.

### [App transaction](/documentation/StoreKit#App-transaction)

[

Supporting business model changes by using the app transaction](/documentation/storekit/supporting-business-model-changes-by-using-the-app-transaction)

Access the app transaction to learn when a customer first purchased an app, to determine the app features they’re entitled to.

```swift
```swift
```swift
struct AppTransaction
```
```

Information that represents the customer’s purchase of the app, cryptographically signed by the App Store.
```

### [Messages](/documentation/StoreKit#Messages)

```swift
```swift
```swift
```swift
struct Message
```
```

An instance for receiving and displaying App Store messages in your app.
```
```swift
```swift
```swift
struct Reason
```
```

Reasons for the App Store messages.
```
```swift
```swift
```swift
struct DisplayMessageAction
```
```

An instance that asks StoreKit to display an App Store message, if appropriate.
```
```

### [Reviews](/documentation/StoreKit#Reviews)

[

Requesting App Store reviews](/documentation/storekit/requesting-app-store-reviews)

Implement best practices for prompting users to review your app in the App Store.

```swift
```swift
```swift
struct RequestReviewAction
```
```

An instance that tells StoreKit to request an App Store rating or review, if appropriate.
```
```swift
```swift
```swift
class SKStoreReviewController
```
```

An object that controls the process of requesting App Store ratings and reviews from customers.

Deprecated
```

### [Recommendations](/documentation/StoreKit#Recommendations)

[

Offering media for sale in your app](/documentation/storekit/offering-media-for-sale-in-your-app)

Allow users to purchase media in the App Store from within your app.

```swift
```swift
```swift
class SKStoreProductViewController
```
```

A view controller that provides a page where customers can purchase media from the App Store.
```
```swift
```swift
```swift
class SKOverlay
```
```

A class that displays an overlay you can use to recommend another app or an App Clip’s corresponding full app.
```

### [Background assets extension](/documentation/StoreKit#Background-assets-extension)

```swift
```swift
```swift
```swift
protocol StoreDownloaderExtension
```
```

A protocol to which a downloader extension for Apple-Hosted Background Assets must conform.

Beta
```
```

### [Payment method binding](/documentation/StoreKit#Payment-method-binding)

```swift
```swift
```swift
```swift
struct PaymentMethodBinding
```
```

A binding that makes payment methods available in apps for an Apple ID.
```
```

### [Ad network attribution](/documentation/StoreKit#Ad-network-attribution)

[

API Reference

Ad network attribution](/documentation/storekit/ad-network-attribution)

Validate advertisement-driven app installations.

### [External Purchase](/documentation/StoreKit#External-Purchase)

[

API Reference

External Purchase](/documentation/storekit/external-purchase)

Enable qualifying apps to offer external purchases.

### [External link account](/documentation/StoreKit#External-link-account)

[

API Reference

External link account](/documentation/storekit/external-link-account)

Enable qualifying apps to link to an external website for account creation or management.

### [Deprecated](/documentation/StoreKit#Deprecated)

```swift
```swift
```swift
```swift
class SKCloudServiceSetupViewController
```
```

A view controller that helps people perform setup for a cloud service, like an Apple Music subscription.

Deprecated
```
```swift
```swift
```swift
class SKCloudServiceController
```
```

An object that determines the current capabilities of a person’s Music library.

Deprecated
```
```

## [See Also](/documentation/StoreKit#see-also)

### [Related Documentation](/documentation/StoreKit#Related-Documentation)

[

App Store Server API](/documentation/AppStoreServerAPI)

Manage your customers’ App Store transactions from your server.

[

StoreKit Test](/documentation/StoreKitTest)

Create and automate tests in Xcode for your app’s subscription and in-app purchase transactions, and SKAdNetwork implementations.

[

App Store Server Notifications](/documentation/AppStoreServerNotifications)

Monitor In-App Purchase events in real time and learn of unreported external purchase tokens, with server notifications from the App Store.

[

App Store Connect API](/documentation/AppStoreConnectAPI)

Automate the tasks you perform on the Apple Developer website and in App Store Connect.

[

App Store Receipts](/documentation/appstorereceipts)

Validate app and In-App Purchase receipts with the App Store.

Deprecated