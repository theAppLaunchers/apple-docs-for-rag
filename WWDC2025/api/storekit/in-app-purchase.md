Collection

*   [StoreKit](/documentation/storekit)
*   In-App Purchase

API Collection

# In-App Purchase

Offer content and services in your app across Apple platforms using a Swift-based interface.

## [Overview](/documentation/StoreKit/in-app-purchase#overview)

With the In-App Purchase API, you can offer customers the opportunity to purchase digital content and services in your app. Customers can make the purchases within your app, and find your promoted products on the App Store.

The StoreKit framework connects to the App Store on your app’s behalf to prompt for, and securely process, payments. The framework then notifies your app, making the transactions for In-App Purchases available to your app on all of the customer’s devices. For each transaction that represents a current purchase, your app delivers the purchased products. To validate purchases, you can verify transactions on your server, or rely on StoreKit’s verification.

![A diagram of the interactions between StoreKit, your app, the App Store, and your server that occur during a transaction.](https://docs-assets.developer.apple.com/published/3cddba76b6de9f552b4afc2d69fd0799/media-4447232%402x.png)

The App Store can also communicate with your server. It notifies your server of transactions and auto-renewable subscription events through [App Store Server Notifications](/documentation/AppStoreServerNotifications), and provides the same transaction information, and more, through the [App Store Server API](/documentation/AppStoreServerAPI).

To learn how adding In-App Purchases fits in an overall app development workflow for the App Store, see [App Store Pathway](https://developer.apple.com/app-store/pathway/). For an overview of In-App Purchases and its features, including its configuration, testing capabilities, marketing for your products, and more, see [Simple and safe In-App Purchases](https://developer.apple.com/in-app-purchase/). For an overview on subscriptions, including creating subscription groups, Family Sharing, and more, see [Auto-renewable subscriptions](https://developer.apple.com/app-store/subscriptions/).

### [Configure In-App Purchases](/documentation/StoreKit/in-app-purchase#Configure-In-App-Purchases)

To use the In-App Purchase API, you first need to configure the products that your app merchandises.

*   In the early stages of development, you can configure the products in the StoreKit configuration file in Xcode, and test your code without any dependency on App Store Connect. For more information, see [Setting up StoreKit Testing in Xcode](/documentation/Xcode/setting-up-storekit-testing-in-xcode).
    
*   When you’re ready for sandbox testing and production, configure the products in App Store Connect. You can add or remove products and refine or reconfigure existing products as you develop your app. For more information, see [Configure In-App Purchase settings](https://developer.apple.com/help/app-store-connect/configure-in-app-purchase-settings/overview-for-configuring-in-app-purchases).
    

You can also offer apps and In-App Purchases that run on multiple platforms as a single purchase. For more information on universal purchase, see [Add platforms](https://developer.apple.com/help/app-store-connect/create-an-app-record/add-platforms/).

### [Support a store in your app](/documentation/StoreKit/in-app-purchase#Support-a-store-in-your-app)

The In-App Purchase API takes advantage of Swift features like concurrency to simplify your In-App Purchase workflows, and SwiftUI to build stores with [StoreKit views](/documentation/storekit/storekit-views). Use the API to manage access to content and subscriptions, receive App Store-signed transaction information, get the history of all In-App Purchase transactions, and more.

Related sessions from WWDC21

Session 10114: [Meet StoreKit 2](https://developer.apple.com/videos/play/wwdc2021/10114/)

The In-App Purchase API offers:

*   Transaction information that’s App Store-signed in JSON Web Signature (JWS) format.
    
*   Transaction and subscription status information that’s simple to parse in your app.
    
*   An entitlements API, [`currentEntitlements`](/documentation/storekit/transaction/currententitlements), that simplifies determining entitlements to unlock content and services for your customers.
    

Related sessions from WWDC22

Session 110404: [Implement proactive in-app purchase restore](https://developer.apple.com/videos/play/wwdc2022/110404/)

To support a store in your app, implement the following functionality:

*   Listen for transaction state changes using the transaction listener, [`updates`](/documentation/storekit/transaction/updates), to provide up-to-date service and content while your app is running.
    
*   Use [StoreKit views](/documentation/storekit/storekit-views) to merchandise your products; or request products to display from the App Store with [`products(for:)`](/documentation/storekit/product/products\(for:\)) and enable purchases using [`purchase(options:)`](/documentation/storekit/product/purchase\(options:\)). Unlock purchased content and services based on the purchase result, [`Product.PurchaseResult`](/documentation/storekit/product/purchaseresult).
    
*   Iterate through a customer’s purchases anytime using the transaction sequence [`all`](/documentation/storekit/transaction/all), and unlock the purchased content and services.
    
*   Optionally, validate the signed transactions and signed subscription status information that you receive from the API.
    

## [Topics](/documentation/StoreKit/in-app-purchase#topics)

### [In-App Purchase merchandising](/documentation/StoreKit/in-app-purchase#In-App-Purchase-merchandising)

[

API Reference

StoreKit views](/documentation/storekit/storekit-views)

Display a customizable In-App Purchase store using StoreKit views for SwiftUI.

### [Product and subscription information](/documentation/StoreKit/in-app-purchase#Product-and-subscription-information)

[

Implementing a store in your app using the StoreKit API](/documentation/storekit/implementing-a-store-in-your-app-using-the-storekit-api)

Offer In-App Purchases and manage entitlements using signed transactions and status information.

```swift
```swift
```swift
struct Product
```
```

Information about a product that you configure in App Store Connect.
```
```swift
```swift
```swift
struct SubscriptionInfo
```
```

Information about an auto-renewable subscription, such as its status, period, subscription group, and subscription offer details.
```
```swift
```swift
```swift
typealias SubscriptionInfo
```
```

Information about an auto-renewable subscription.
```
```swift
```swift
```swift
typealias SubscriptionStatus
```
```

Represents the renewal status information for an auto-renewable subscription.
```

### [Purchase requests and results](/documentation/StoreKit/in-app-purchase#Purchase-requests-and-results)

```swift
```swift
```swift
```swift
struct PurchaseAction
```
```

An action that starts an In-App Purchase.
```
```swift
```swift
```swift
func purchase(options: Set<Product.PurchaseOption>) async throws -> Product.PurchaseResult
```
```

Initiates a purchase for the product with the App Store and displays the confirmation sheet.
```
```swift
```swift
```swift
enum PurchaseResult
```
```

The result of a purchase.
```
```

### [Transaction history and entitlements](/documentation/StoreKit/in-app-purchase#Transaction-history-and-entitlements)

```swift
```swift
```swift
```swift
struct Transaction
```
```

Information that represents the customer’s purchase of a product in your app.
```

[`static var updates: Transaction.Transactions`](/documentation/storekit/transaction/updates)

The asynchronous sequence that emits a transaction when the system creates or updates transactions that occur outside the app or on other devices.

[`static var all: Transaction.Transactions`](/documentation/storekit/transaction/all)

A sequence that emits all the customer’s transactions for your app.

[`static var currentEntitlements: Transaction.Transactions`](/documentation/storekit/transaction/currententitlements)

A sequence of the latest transactions that entitle a customer to In-App Purchases and subscriptions.
```

### [JWS verification](/documentation/StoreKit/in-app-purchase#JWS-verification)

```swift
```swift
```swift
```swift
enum VerificationResult
```
```

A type that describes the result of a StoreKit verification.
```
```swift
```swift
```swift
enum VerificationError
```
```

Error cases for StoreKit JWS verification.
```
```

### [Subscription status and renewal information](/documentation/StoreKit/in-app-purchase#Subscription-status-and-renewal-information)

```swift
```swift
```swift
```swift
struct Status
```
```

The renewal status information for an auto-renewable subscription.
```
```swift
```swift
```swift
struct RenewalInfo
```
```

The renewal information for an auto-renewable subscription.
```
```swift
```swift
```swift
typealias SubscriptionRenewalInfo
```
```

Represents the renewal information for an auto-renewable subscription.
```
```swift
```swift
```swift
struct RenewalState
```
```

The renewal states of auto-renewable subscriptions.
```
```swift
```swift
```swift
typealias SubscriptionRenewalState
```
```

The renewal states of auto-renewable subscriptions.
```
```swift
```swift
```swift
typealias SubscriptionPeriod
```
```

Represents the duration of time between subscription renewals.
```
```

### [Subscription offers and offer codes](/documentation/StoreKit/in-app-purchase#Subscription-offers-and-offer-codes)

[

Supporting win-back offers in your app](/documentation/storekit/supporting-win-back-offers-in-your-app)

Re-engage previous subscribers with a free or discounted offer for an auto-renewable subscription, for a specific duration.

[

Merchandising win-back offers in your app](/documentation/storekit/merchandising-win-back-offers-in-your-app)

Present win-back offers to eligible customers in your app with the win-back offer sheet or by implementing custom merchandising.

[

Supporting subscription offer codes in your app](/documentation/storekit/supporting-subscription-offer-codes-in-your-app)

Provide subscription service for customers who redeem offer codes through the App Store or within your app.

```swift
```swift
```swift
struct SubscriptionOffer
```
```

Information about a subscription offer that you configure in App Store Connect.
```
```swift
```swift
```swift
struct OfferType
```
```

The types of offers for auto-renewable subscriptions.
```

### [Promoted In-App Purchases](/documentation/StoreKit/in-app-purchase#Promoted-In-App-Purchases)

[

Supporting promoted In-App Purchases in your app](/documentation/storekit/supporting-promoted-in-app-purchases-in-your-app)

Display promoted In-App Purchases on your product page and handle purchases that users initiate on the App Store.

```swift
```swift
```swift
struct PurchaseIntent
```
```

An instance that emits purchase intents, which indicate that the customer initiated a purchase outside of your app, for your app to complete.
```
```swift
```swift
```swift
struct PromotionInfo
```
```

Information about a promoted In-App Purchase that customizes its order and visibility on the device.
```

[

Testing promoted In-App Purchases](/documentation/storekit/testing-promoted-in-app-purchases)

Test your In-App Purchases before making your app available in the App Store.

### [App Store interactions](/documentation/StoreKit/in-app-purchase#App-Store-interactions)

```swift
```swift
```swift
```swift
enum AppStore
```
```

Interactions with the App Store, such as managing subscriptions, verifying devices, authorizing payments, synchronizing transactions, getting the environment, and more.
```
```swift
```swift
```swift
struct AppTransaction
```
```

Information that represents the customer’s purchase of the app, cryptographically signed by the App Store.
```
```

### [Storefront information](/documentation/StoreKit/in-app-purchase#Storefront-information)

```swift
```swift
```swift
```swift
struct Storefront
```
```

The region and unique identifier of the App Store storefront for the device.
```

[`static var current: Storefront?`](/documentation/storekit/storefront/current)

The current App Store storefront for product purchases.

[`static var updates: Storefront.Storefronts`](/documentation/storekit/storefront/updates)

The asynchronous sequence that emits storefront information when the system updates the storefront.
```

### [In-App Purchase Testing](/documentation/StoreKit/in-app-purchase#In-App-Purchase-Testing)

[

Testing at all stages of development with Xcode and the sandbox](/documentation/storekit/testing-at-all-stages-of-development-with-xcode-and-the-sandbox)

Verify your implementation of In-App Purchases by testing your code throughout its development.

[

Testing In-App Purchases with sandbox](/documentation/storekit/testing-in-app-purchases-with-sandbox)

Test your implementation of In-App Purchases using real product information and server-to-server transactions in the sandbox environment.

[

Testing refund requests](/documentation/storekit/testing-refund-requests)

Test your app’s implementation of refund requests, and your app’s and server’s handling of approved and declined refunds.

[

Testing win-back offers in Xcode](/documentation/storekit/testing-win-back-offers-in-xcode)

Validate your app’s handling of win-back offers that you configure for the testing environment.

### [Advanced Commerce API interactions](/documentation/StoreKit/in-app-purchase#Advanced-Commerce-API-interactions)

```swift
```swift
```swift
```swift
struct AdvancedCommerceProduct
```
```

A product configured as a generic SKU in App Store Connect for use with the Advanced Commerce API.
```

[

Sending Advanced Commerce API requests from your app](/documentation/storekit/sending-advanced-commerce-api-requests-from-your-app)

Send Advanced Commerce API requests from your app that you authorize with a JSON Web Signature (JWS) you generate on your server.

[

Generating JWS to sign App Store requests](/documentation/storekit/generating-jws-to-sign-app-store-requests)

Create signed JSON Web Signature (JWS) strings on your server to authorize your API requests in your app.
```

### [Errors](/documentation/StoreKit/in-app-purchase#Errors)

```swift
```swift
```swift
```swift
enum StoreKitError
```
```

StoreKit In-App Purchase error codes.
```
```

### [Deprecated](/documentation/StoreKit/in-app-purchase#Deprecated)

[

Choosing a StoreKit API for In-App Purchases](/documentation/storekit/choosing-a-storekit-api-for-in-app-purchases)

Use the latest API to support In-App Purchases in new or existing apps, or the original API to support In-App Purchases in earlier operating systems.

[

API Reference

Original API for In-App Purchase](/documentation/storekit/original-api-for-in-app-purchase)

Offer additional content and services in your app using the Original In-App Purchase API.

## [See Also](/documentation/StoreKit/in-app-purchase#see-also)

### [In-App Purchase](/documentation/StoreKit/in-app-purchase#In-App-Purchase)

[

Understanding StoreKit workflows](/documentation/storekit/understanding-storekit-workflows)

Implement an in-app store with several product types, using StoreKit views.

[

Getting started with In-App Purchase using StoreKit views](/documentation/storekit/getting-started-with-in-app-purchases-using-storekit-views)

Set up an in-app store using SwiftUI and StoreKit views.