*   [StoreKit](/documentation/storekit)
*   Transaction

Structure

# Transaction

Information that represents the customer’s purchase of a product in your app.

iOS 15.0+iPadOS 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
struct Transaction
```
```
```
```
```
```
```
```

## [Mentioned in](/documentation/StoreKit/Transaction#mentions)

[

Supporting subscription offer codes in your app](/documentation/storekit/supporting-subscription-offer-codes-in-your-app)

[

Supporting win-back offers in your app](/documentation/storekit/supporting-win-back-offers-in-your-app)

[

Testing win-back offers in the sandbox environment](/documentation/storekit/testing-win-back-offers-in-the-sandbox-environment)

[

Testing purchases made outside your app](/documentation/storekit/testing-purchases-made-outside-your-app)

[

Validating receipts with the App Store](/documentation/storekit/validating-receipts-with-the-app-store)

## [Overview](/documentation/StoreKit/Transaction#overview)

A _transaction_ represents a successful In-App Purchase. The App Store generates a transaction each time a customer purchases an In-App Purchase product or renews a subscription. For each transaction that represents a current purchase, your app unlocks the purchased content or service and finishes the transaction.

Use the `Transaction` type to perform these transaction-related tasks:

*   Get the customer’s transaction history, latest transactions, and current entitlements to unlock content and services.
    
*   Access transaction properties.
    
*   Finish a transaction after your app delivers the purchased content or service.
    
*   Access the raw JSON Web Signature (JWS) string and supporting values to verify the transaction information.
    
*   Listen for new transactions while the app is running.
    
*   Begin a refund request from within your app.
    

### [Access transaction history and current entitlements](/documentation/StoreKit/Transaction#Access-transaction-history-and-current-entitlements)

Your app doesn’t create transaction objects. Instead, StoreKit automatically makes up-to-date transactions available to your app, including when someone launches the app for the first time.

Related sessions from WWDC22

Session 110404: [Implement proactive in-app purchase restore](https://developer.apple.com/videos/play/wwdc2022/110404/)

You access transactions in several ways:

*   Get transaction history anytime by accessing the static [`all`](/documentation/storekit/transaction/all) sequence, or get just the most recent transaction for a product with the [`latestTransaction`](/documentation/storekit/product/latesttransaction) property of [`Product`](/documentation/storekit/product).
    
*   Receive notifications for new transactions while your app is running when customers complete a purchase outside of the app, including on another device, through the transaction listener, [`updates`](/documentation/storekit/transaction/updates).
    
*   Access the latest transaction for a subscription group through the subscription status API, using [`transaction`](/documentation/storekit/product/subscriptioninfo/status-swift.struct/transaction).
    
*   After a successful In-App Purchase, StoreKit returns the transaction through [`Product.PurchaseResult.success(_:)`](/documentation/storekit/product/purchaseresult/success\(_:\)).
    

The most important use of transaction information is for determining which In-App Purchases the customer has paid access to, so your app can unlock the content or service. The [`currentEntitlements`](/documentation/storekit/transaction/currententitlements) API provides the information you need to unlock all of the customer’s paid content in your app. Use `currentEntitlements` to get a list of transactions for all the products the customer is currently entitled to, including non-consumable In-App Purchases and currently active subscriptions.

### [Verify transactions](/documentation/StoreKit/Transaction#Verify-transactions)

The App Store cryptographically signs transaction information in JWS format. StoreKit automatically validates and returns the signed information, wrapped in a [`VerificationResult`](/documentation/storekit/verificationresult). When the `VerificationResult` wraps a `Transaction` value, it provides the raw JWS string in the [`jwsRepresentation`](/documentation/storekit/verificationresult/jwsrepresentation-21vgo) property. If you get a transaction through [`VerificationResult.verified(_:)`](/documentation/storekit/verificationresult/verified\(_:\)), the information passed validation. If you get it through [`VerificationResult.unverified(_:_:)`](/documentation/storekit/verificationresult/unverified\(_:_:\)), the information didn’t pass StoreKit’s automatic validation. Your app can immediately access the transaction information in the [Transaction properties](/documentation/storekit/transaction-properties).

To perform your own validation on the device, use the verification result’s [`jwsRepresentation`](/documentation/storekit/verificationresult/jwsrepresentation-21vgo) string, and use the provided convenience properties [`headerData`](/documentation/storekit/verificationresult/headerdata-9egfp), [`payloadData`](/documentation/storekit/verificationresult/payloaddata-uyle), and [`signatureData`](/documentation/storekit/verificationresult/signaturedata-4pyv8). For added control and security, send the `jwsRepresentation` to your server to verify. Consider using the App Store Server Library to implement your verification. The library provides the functions `verifyAndDecodeTransaction` and `verifyAndDecodeRenewalInfo` in each language the library supports. For more information, see [Simplifying your implementation by using the App Store Server Library](/documentation/AppStoreServerAPI/simplifying-your-implementation-by-using-the-app-store-server-library).

Tip

The [`jwsRepresentation`](/documentation/storekit/verificationresult/jwsrepresentation-21vgo) is the same as the [`JWSTransaction`](/documentation/AppStoreServerAPI/JWSTransaction) that the [App Store Server API](/documentation/AppStoreServerAPI) returns and to the [`JWSTransaction`](/documentation/AppStoreServerNotifications/JWSTransaction) that you receive in [`App Store Server Notifications V2`](/documentation/AppStoreServerNotifications/App-Store-Server-Notifications-V2). You can validate them on your server in the same way.

If StoreKit returns a transaction as verified, the transaction is valid for the device. For information about performing your own verification for a device, see [`deviceVerification`](/documentation/storekit/transaction/deviceverification).

For more information about JWS, see the [IETF RFC 7515](https://datatracker.ietf.org/doc/html/rfc7515) specification.

### [Access purchases made with the original API](/documentation/StoreKit/Transaction#Access-purchases-made-with-the-original-API)

All In-App Purchases that customers make are equally available to your app in this `Transaction` API, and in receipts using the [Original API for In-App Purchase](/documentation/storekit/original-api-for-in-app-purchase), as follows:

*   New purchases that customers make with the original API are available immediately using the `Transaction` API.
    
*   Purchases that customers make with the [`purchase(options:)`](/documentation/storekit/product/purchase\(options:\)) method are available in the original API when your app refreshes the receipt. For more information, see [`SKReceiptRefreshRequest`](/documentation/storekit/skreceiptrefreshrequest).
    

## [Topics](/documentation/StoreKit/Transaction#topics)

### [Transaction properties](/documentation/StoreKit/Transaction#Transaction-properties)

[

API Reference

Transaction properties](/documentation/storekit/transaction-properties)

The properties of a transaction, including identifiers, purchase and revocation dates and details, status, and offer details.

```swift
```swift
```swift
var appTransactionID: String
```
```

The unique identifier of the app download transaction.
```

### [Monitoring transaction-related changes](/documentation/StoreKit/Transaction#Monitoring-transaction-related-changes)

[`static var updates: Transaction.Transactions`](/documentation/storekit/transaction/updates)

The asynchronous sequence that emits a transaction when the system creates or updates transactions that occur outside the app or on other devices.

```swift
```swift
```swift
struct Transactions
```
```

An asynchronous sequence of transactions.
```

### [Getting transaction history](/documentation/StoreKit/Transaction#Getting-transaction-history)

[`static func latest(for: String) async -> VerificationResult<Transaction>?`](/documentation/storekit/transaction/latest\(for:\))

Gets the customer’s most recent transaction for an In-App Purchase.

[`static var all: Transaction.Transactions`](/documentation/storekit/transaction/all)

A sequence that emits all the customer’s transactions for your app.

[`static var unfinished: Transaction.Transactions`](/documentation/storekit/transaction/unfinished)

A sequence that emits unfinished transactions for the customer.

[`SKIncludeConsumableInAppPurchaseHistory`](/documentation/BundleResources/Information-Property-List/SKIncludeConsumableInAppPurchaseHistory)

A Boolean value that determines whether StoreKit includes finished consumable In-App Purchases in transaction information.

### [Getting current entitlements](/documentation/StoreKit/Transaction#Getting-current-entitlements)

[`static var currentEntitlements: Transaction.Transactions`](/documentation/storekit/transaction/currententitlements)

A sequence of the latest transactions that entitle a customer to In-App Purchases and subscriptions.

[`static func currentEntitlement(for: String) async -> VerificationResult<Transaction>?`](/documentation/storekit/transaction/currententitlement\(for:\))

Gets the latest transactions that entitle the customer to a specified product.

Deprecated

### [Finishing the transaction](/documentation/StoreKit/Transaction#Finishing-the-transaction)

```swift
```swift
```swift
```swift
func finish() async
```
```

Indicates to the App Store that the app delivered the purchased content or enabled the service to finish the transaction.
```

[`static var unfinished: Transaction.Transactions`](/documentation/storekit/transaction/unfinished)

A sequence that emits unfinished transactions for the customer.
```

### [Verifying transactions](/documentation/StoreKit/Transaction#Verifying-transactions)

```swift
```swift
```swift
```swift
let deviceVerification: Data
```
```

The device verification value you use to verify whether the transaction belongs to the device.
```
```swift
```swift
```swift
let deviceVerificationNonce: UUID
```
```

The UUID for computing the device verification value.
```
```swift
```swift
```swift
let signedDate: Date
```
```

The date that the App Store signed the JWS transaction.
```
```

### [Getting transaction info in JSON format](/documentation/StoreKit/Transaction#Getting-transaction-info-in-JSON-format)

```swift
```swift
```swift
```swift
var jsonRepresentation: Data
```
```

The JSON representation of the transaction information.
```
```

### [Requesting refunds](/documentation/StoreKit/Transaction#Requesting-refunds)

[

Testing refund requests](/documentation/storekit/testing-refund-requests)

Test your app’s implementation of refund requests, and your app’s and server’s handling of approved and declined refunds.

```swift
```swift
```swift
func beginRefundRequest(in: UIWindowScene) async throws -> Transaction.RefundRequestStatus
```
```

Presents the refund request sheet for the transaction in a window scene.
```
```swift
```swift
```swift
func beginRefundRequest(in: NSViewController) async throws -> Transaction.RefundRequestStatus
```
```

Presents the refund request sheet for the transaction in a view controller.
```

[`static func beginRefundRequest(for: UInt64, in: UIWindowScene) async throws -> Transaction.RefundRequestStatus`](/documentation/storekit/transaction/beginrefundrequest\(for:in:\)-65tph)

Presents the refund request sheet for the specified transaction in a window scene.

[`static func beginRefundRequest(for: UInt64, in: NSViewController) async throws -> Transaction.RefundRequestStatus`](/documentation/storekit/transaction/beginrefundrequest\(for:in:\)-9mscy)

Presents the refund request sheet for the specified transaction in a view controller.

```swift
```swift
```swift
enum RefundRequestError
```
```

The error codes for refund requests.
```
```swift
```swift
```swift
enum RefundRequestStatus
```
```

The status codes for refund requests.
```

### [Structures](/documentation/StoreKit/Transaction#Structures)

```swift
```swift
```swift
```swift
struct AdvancedCommerceInfo
```
```

Metadata for transactions that use the Advanced Commerce API.
```
```swift
```swift
```swift
struct OfferType
```
```

The types of subscription offers for auto-renewable subscriptions.
```
```

### [Instance Properties](/documentation/StoreKit/Transaction#Instance-Properties)

```swift
```swift
```swift
```swift
let advancedCommerceInfo: Transaction.AdvancedCommerceInfo?
```
```

Metadata for transactions that use the Advanced Commerce API.
```
```swift
```swift
```swift
var offerPeriodStringRepresentation: String?
```
```

The string representation of the offer period applied to the subscription offer for this transaction.

Deprecated
```
```

### [Type Methods](/documentation/StoreKit/Transaction#Type-Methods)

[`static func all(for: String) -> Transaction.Transactions`](/documentation/storekit/transaction/all\(for:\))

Gets all the transactions associated with this product ID.

[`static func currentEntitlements(for: String) -> Transaction.Transactions`](/documentation/storekit/transaction/currententitlements\(for:\))

Gets the transactions that entitle the user to items purchased under a product ID.

## [Relationships](/documentation/StoreKit/Transaction#relationships)

### [Conforms To](/documentation/StoreKit/Transaction#conforms-to)

*   [`Copyable`](/documentation/Swift/Copyable)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`Identifiable`](/documentation/Swift/Identifiable)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)

## [See Also](/documentation/StoreKit/Transaction#see-also)

### [Transaction history and entitlements](/documentation/StoreKit/Transaction#Transaction-history-and-entitlements)

[`static var updates: Transaction.Transactions`](/documentation/storekit/transaction/updates)

The asynchronous sequence that emits a transaction when the system creates or updates transactions that occur outside the app or on other devices.

[`static var all: Transaction.Transactions`](/documentation/storekit/transaction/all)

A sequence that emits all the customer’s transactions for your app.

[`static var currentEntitlements: Transaction.Transactions`](/documentation/storekit/transaction/currententitlements)

A sequence of the latest transactions that entitle a customer to In-App Purchases and subscriptions.