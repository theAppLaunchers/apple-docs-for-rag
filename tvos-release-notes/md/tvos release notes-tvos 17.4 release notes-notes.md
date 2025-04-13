

- tvOS Release Notes
-  tvOS 17.4 Release Notes 

Article

# tvOS 17.4 Release Notes

Update your apps to use new features, and test your apps against API changes.

## Overview

The tvOS 17.4 SDK provides support to develop tvOS apps for Apple TV devices running tvOS 17.4. The SDK comes bundled with Xcode 15.3, available from the Mac App Store. For information on the compatibility requirements for Xcode 15.3, see Xcode 15.3 Release Notes.

### StoreKit

#### New Features

- `productDescriptionHidden(_:)` API can be used to configure the visibility of product descriptions in `ProductView`, `StoreView` and `SubscriptionStoreView` instances within a view hierarchy. When building with Xcode 15.3, the view modifier can be used even if your app is running on iOS 17.0, iPadOS 17.0, macOS 14.0, tvOS 17.0, watchOS 10.0, visionOS 1.0, or later.

  When implementing a product view style, it can support this new view modifier by checking the `descriptionVisibility` property on the configuration value. (110414819) (FB12261973)

- You can use SubscriptionStoreView to present promotional offers by adding the `subscriptionPromotionalOffer(offer:signature:)` modifier.

  If you’re already using inAppPurchaseOptions(_:) modifier to support promotional offers for StoreKit views, you should adopt the new API instead when your app is running on iOS 17.4, iPadOS 17.4, macOS 14.4, tvOS 17.4, watchOS 10.4, visionOS 1.1 or later. Do not use both APIs to apply a promotional offer for the same view. (115358806)

#### Resolved Issues

- Fixed: The isEligibleForIntroOffer property and isEligibleForIntroOffer(for:) method now reflect ineligibility in cases where a customer would otherwise be eligible for the offer if they weren’t actively subscribed. This means a customer which is not currently eligible for an introductory offer may become eligible in the future.

  Customers who redeem an introductory offer for a given subscription group will continue to never be eligible for another introductory offer in that subscription group. You can detect this case this by checking if any one transaction with a matching subscriptionGroupID has the type property on offer set to introductory. (103604770) (FB11889732)

### SwiftUI

#### Resolved Issues

- Fixed: Resolved an issue with programmatically present an alert or sheet simultaneously with dismissing another sheet. The new alert or sheet would not show but now it will. If you have code that presents the same sheet programmatically from multiple places in your view hierarchy at the same time, that sheet might no longer appear. Make sure that any `sheet` modifiers that are in the view hierarchy at the same time use distinct `isPresented` or `item` bindings. (117475214)

## See Also

### tvOS 17

tvOS 17.6 Release Notes

Update your apps to use new features, and test your apps against API changes.

tvOS 17.5 Release Notes

Update your apps to use new features, and test your apps against API changes.

tvOS 17.3 Release Notes

Update your apps to use new features, and test your apps against API changes.

tvOS 17.2 Release Notes

Update your apps to use new features, and test your apps against API changes.

tvOS 17.1 Release Notes

Update your apps to use new features, and test your apps against API changes.

tvOS 17 Release Notes

Update your apps to use new features, and test your apps against API changes.

