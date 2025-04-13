

- watchOS Release Notes
-  watchOS 10.4 Release Notes 

Article

# watchOS 10.4 Release Notes

Update your apps to use new features, and test your apps against API changes.

## Overview

The watchOS 10.4 SDK provides support to develop watchOS apps for Apple Watch devices running watchOS 10.4. The SDK comes bundled with Xcode 15.3, available from the Mac App Store. For information on the compatibility requirements for Xcode 15.3, see Xcode 15.3 Release Notes.

### Movement Disorder API

#### Resolved Issues

- Fixed: The MovementDisorder API will return a new error code if tremor and dyskinesia data was not saved to the user’s device between queries. This is to help identify data loss when tracking the availability of metrics. (41729033)

### StoreKit

#### New Features

- `productDescriptionHidden(_:)` API can be used to configure the visibility of product descriptions in `ProductView`, `StoreView` and `SubscriptionStoreView` instances within a view hierarchy. When building with Xcode 15.3, the view modifier can be used even if your app is running on iOS 17.0, iPadOS 17.0, macOS 14.0, tvOS 17.0, watchOS 10.0, visionOS 1.0, or later.

  When implementing a product view style, it can support this new view modifier by checking the `descriptionVisibility` property on the configuration value. (110414819) (FB12261973)

- You can use SubscriptionStoreView to present promotional offers by adding the `subscriptionPromotionalOffer(offer:signature:)` modifier.

  If you’re already using inAppPurchaseOptions(_:) modifier to support promotional offers for StoreKit views, you should adopt the new API instead when your app is running on iOS 17.4, iPadOS 17.4, macOS 14.4, tvOS 17.4, watchOS 10.4, visionOS 1.1 or later. Do not use both APIs to apply a promotional offer for the same view. (115358806)

#### Resolved Issues

- Fixed: The isEligibleForIntroOffer property and isEligibleForIntroOffer(for:) method now reflect ineligibility in cases where a customer would otherwise be eligible for the offer if they weren’t actively subscribed. This means a customer which is not currently eligible for an introductory offer may become eligible in the future.

  Customers who redeem an introductory offer for a given subscription group will continue to never be eligible for another introductory offer in that subscription group. You can detect this case this by checking if any one transaction with a matching subscriptionGroupID has the type property on offer set to introductory. (103604770) (FB11889732)

## See Also

### watchOS 10

watchOS 10.6 Release Notes

Update your apps to use new features, and test your apps against API changes.

watchOS 10.5 Release Notes

Update your apps to use new features, and test your apps against API changes.

watchOS 10.3 Release Notes

Update your apps to use new features, and test your apps against API changes.

watchOS 10.2 Release Notes

Update your apps to use new features, and test your apps against API changes.

watchOS 10.1 Release Notes

Update your apps to use new features, and test your apps against API changes.

watchOS 10 Release Notes

Update your apps to use new features, and test your apps against API changes.

