*   [App Store Server Notifications](/documentation/appstoreservernotifications)
*   App Store Server Notifications changelog

Article

# App Store Server Notifications changelog

Learn about changes to the App Store Server Notifications service.

## [Overview](/documentation/AppStoreServerNotifications/app-store-server-notifications-changelog#overview)

App Store Server Notifications has two versions of notifications. Version 1 notifications and the [`App Store Server Notifications V1`](/documentation/appstoreservernotifications/app-store-server-notifications-v1) endpoint are deprecated. Instead, implement the [`App Store Server Notifications V2`](/documentation/appstoreservernotifications/app-store-server-notifications-v2) endpoint on your server to receive version 2 notifications.

To set up your server to receive notifications, see [Enabling App Store Server Notifications](/documentation/appstoreservernotifications/enabling-app-store-server-notifications). Use this changelog to learn about feature updates, version information, deprecations, and removals for App Store Server Notifications.

### [May 27, 2025](/documentation/AppStoreServerNotifications/app-store-server-notifications-changelog#May-27-2025)

**New features**

*   The `ONE_TIME_CHARGE` [`notificationType`](/documentation/appstoreservernotifications/notificationtype) is now available in the production environment.
    

### [March 24, 2025](/documentation/AppStoreServerNotifications/app-store-server-notifications-changelog#March-24-2025)

**New features**

*   Added the notification types `METADATA_UPDATE` and `MIGRATE` to [`notificationType`](/documentation/appstoreservernotifications/notificationtype).
    
*   Added the [`previousOriginalTransactionId`](/documentation/appstoreservernotifications/previousoriginaltransactionid) field to the [`JWSTransactionDecodedPayload`](/documentation/appstoreservernotifications/jwstransactiondecodedpayload).
    

### [February 21, 2025](/documentation/AppStoreServerNotifications/app-store-server-notifications-changelog#February-21-2025)

**New features**

*   Updated the [`JWSRenewalInfoDecodedPayload`](/documentation/appstoreservernotifications/jwsrenewalinfodecodedpayload) and [`JWSTransactionDecodedPayload`](/documentation/appstoreservernotifications/jwstransactiondecodedpayload) to include the new [`appTransactionId`](/documentation/appstoreservernotifications/apptransactionid) and [`offerPeriod`](/documentation/appstoreservernotifications/offerperiod) fields.
    
*   Updated the [`JWSRenewalInfoDecodedPayload`](/documentation/appstoreservernotifications/jwsrenewalinfodecodedpayload) to include the [`appAccountToken`](/documentation/appstoreservernotifications/appaccounttoken) field.
    

### [January 17, 2025](/documentation/AppStoreServerNotifications/app-store-server-notifications-changelog#January-17-2025)

**New features**

*   Added support for the [Advanced Commerce API](/documentation/AdvancedCommerceAPI).
    

### [July 8, 2024](/documentation/AppStoreServerNotifications/app-store-server-notifications-changelog#July-8-2024)

**New features**

*   Updated the [`JWSRenewalInfoDecodedPayload`](/documentation/appstoreservernotifications/jwsrenewalinfodecodedpayload) to include the new field [`eligibleWinBackOfferIds`](/documentation/appstoreservernotifications/eligiblewinbackofferids).
    
*   Added the win-back offer type to [`offerType`](/documentation/appstoreservernotifications/offertype).
    

### [June 10, 2024](/documentation/AppStoreServerNotifications/app-store-server-notifications-changelog#June-10-2024)

**New features**

*   Added the notification type `ONE_TIME_CHARGE` to [`notificationType`](/documentation/appstoreservernotifications/notificationtype). This notification type is currently available only in the sandbox environment.
    
*   Added the fields [`renewalPrice`](/documentation/AppStoreServerAPI/renewalPrice), [`currency`](/documentation/appstoreservernotifications/currency), and [`offerDiscountType`](/documentation/appstoreservernotifications/offerdiscounttype) to the [`JWSRenewalInfoDecodedPayload`](/documentation/appstoreservernotifications/jwsrenewalinfodecodedpayload).
    

### [April 11, 2024](/documentation/AppStoreServerNotifications/app-store-server-notifications-changelog#April-11-2024)

**New features**

*   Added the [`consumptionRequestReason`](/documentation/appstoreservernotifications/consumptionrequestreason) to the [`data`](/documentation/appstoreservernotifications/data) object.
    
*   The `CONSUMPTION_REQUEST` [`notificationType`](/documentation/appstoreservernotifications/notificationtype) added notifications for refund requests for auto-renewable subscriptions.
    

### [March 12, 2024](/documentation/AppStoreServerNotifications/app-store-server-notifications-changelog#March-12-2024)

**New features**

*   The type of the [`price`](/documentation/appstoreservernotifications/price) field changed from `int32` to `int64`.
    

### [February 29, 2024](/documentation/AppStoreServerNotifications/app-store-server-notifications-changelog#February-29-2024)

**New features**

*   Added a new [`notificationType`](/documentation/appstoreservernotifications/notificationtype): `EXTERNAL_PURCHASE_TOKEN` and a [`subtype`](/documentation/appstoreservernotifications/subtype): `UNREPORTED`.
    
*   Updated the [`responseBodyV2DecodedPayload`](/documentation/appstoreservernotifications/responsebodyv2decodedpayload) to include the new payload object, [`externalPurchaseToken`](/documentation/appstoreservernotifications/externalpurchasetoken).
    
*   Added the types [`externalPurchaseId`](/documentation/appstoreservernotifications/externalpurchaseid) and [`tokenCreationDate`](/documentation/appstoreservernotifications/tokencreationdate).
    

### [January 23, 2024](/documentation/AppStoreServerNotifications/app-store-server-notifications-changelog#January-23-2024)

**New features**

*   Changed the notification type the App Store server sends when a customer redeems a subscription offer for an inactive subscription to the `SUBSCRIBED` [`notificationType`](/documentation/appstoreservernotifications/notificationtype). The App Store server only sends the `OFFER_REDEEMED` notification type when customers redeem an offer on an active subscription.
    

### [October 26, 2023](/documentation/AppStoreServerNotifications/app-store-server-notifications-changelog#October-26-2023)

**New features**

*   Added new properties in the [`JWSTransactionDecodedPayload`](/documentation/appstoreservernotifications/jwstransactiondecodedpayload) object: [`price`](/documentation/appstoreservernotifications/price), [`currency`](/documentation/appstoreservernotifications/currency), and [`offerDiscountType`](/documentation/appstoreservernotifications/offerdiscounttype).
    

### [June 5, 2023](/documentation/AppStoreServerNotifications/app-store-server-notifications-changelog#June-5-2023)

**New features**

*   Added a new version 2 [`notificationType`](/documentation/appstoreservernotifications/notificationtype), `REFUND_REVERSED`.
    
*   Added the following new fields in the transaction decoded payload, [`JWSTransactionDecodedPayload`](/documentation/appstoreservernotifications/jwstransactiondecodedpayload): [`storefront`](/documentation/appstoreservernotifications/storefront), [`storefrontId`](/documentation/appstoreservernotifications/storefrontid), and [`transactionReason`](/documentation/appstoreservernotifications/transactionreason).
    
*   Added the `renewalDate` field in the renewal info decoded payload, [`JWSRenewalInfoDecodedPayload`](/documentation/appstoreservernotifications/jwsrenewalinfodecodedpayload).
    
*   Added a subscription [`status`](/documentation/appstoreservernotifications/status) field in the [`data`](/documentation/appstoreservernotifications/data) object of the [`responseBodyV2DecodedPayload`](/documentation/appstoreservernotifications/responsebodyv2decodedpayload).
    
*   The [`responseBodyV1`](/documentation/appstoreservernotifications/responsebodyv1) now includes a `deprecation` field.
    

**Deprecations**

*   The [`App Store Server Notifications V1`](/documentation/appstoreservernotifications/app-store-server-notifications-v1) endpoint and version 1 notifications are deprecated. Implement the [`App Store Server Notifications V2`](/documentation/appstoreservernotifications/app-store-server-notifications-v2) endpoint on your server to receive version 2 notifications instead.
    

### [January 30, 2023](/documentation/AppStoreServerNotifications/app-store-server-notifications-changelog#January-30-2023)

**New features**

*   Added a new notification type for App Store Server Notifications 2 that consists of the [`notificationType`](/documentation/appstoreservernotifications/notificationtype) value `RENEWAL_EXTENSION` and [`subtype`](/documentation/appstoreservernotifications/subtype) values of `SUMMARY` and `FAILURE`. This notification provides information when you extend the subscription renewal date for all active subscribers, based on a product identifier. For more information, see [`Extend Subscription Renewal Dates for All Active Subscribers`](/documentation/AppStoreServerAPI/Extend-Subscription-Renewal-Dates-for-All-Active-Subscribers) in the [App Store Server API](/documentation/AppStoreServerAPI).
    
*   Updated the [`responseBodyV2DecodedPayload`](/documentation/appstoreservernotifications/responsebodyv2decodedpayload) to include the new [`summary`](/documentation/appstoreservernotifications/summary) object, which appears in the payload for a `RENEWAL_EXTENSION` notification with a `SUMMARY` [`subtype`](/documentation/appstoreservernotifications/subtype).
    

### [November 7, 2022](/documentation/AppStoreServerNotifications/app-store-server-notifications-changelog#November-7-2022)

**New features**

*   Added the `PRODUCT_NOT_FOR_SALE` [`subtype`](/documentation/appstoreservernotifications/subtype) for the `EXPIRED` [`notificationType`](/documentation/appstoreservernotifications/notificationtype).
    

### [June 6, 2022](/documentation/AppStoreServerNotifications/app-store-server-notifications-changelog#June-6-2022)

**New features**

*   App Store Server Notifications 2 supports sending a `TEST` notification. For more information, see [`notificationType`](/documentation/appstoreservernotifications/notificationtype), and the endpoints [`Request a Test Notification`](/documentation/AppStoreServerAPI/Request-a-Test-Notification) and [`Get Test Notification Status`](/documentation/AppStoreServerAPI/Get-Test-Notification-Status) in the [App Store Server API](/documentation/AppStoreServerAPI).
    

### [May 12, 2022](/documentation/AppStoreServerNotifications/app-store-server-notifications-changelog#May-12-2022)

**New features**

*   In App Store Server Notifications 2, the notification subtype `ACCEPTED` is now sent when the App Store notifies the customer of an auto-renewable subscription price increase that doesn’t require customer consent. This notification subtype is available only in version 2 notifications. For more information, see [`subtype`](/documentation/appstoreservernotifications/subtype).
    

### [October 21, 2021 - version 2](/documentation/AppStoreServerNotifications/app-store-server-notifications-changelog#October-21-2021-version-2)

**New features**

*   [`App Store Server Notifications V2`](/documentation/appstoreservernotifications/app-store-server-notifications-v2) is available, and version 1 is still supported. For information about the notifications sent in version 2, see [`notificationType`](/documentation/appstoreservernotifications/notificationtype), `substate`, and [`responseBodyV2`](/documentation/appstoreservernotifications/responsebodyv2).
    
*   For information about the notifications sent in version 1, see [`notification_type`](/documentation/appstoreservernotifications/notification_type) and [`responseBodyV1`](/documentation/appstoreservernotifications/responsebodyv1) (previously named `responseBody`).
    

### [March 10, 2021](/documentation/AppStoreServerNotifications/app-store-server-notifications-changelog#March-10-2021)

**Deprecations**

*   In [App Store Server Notifications Version 1](/documentation/appstoreservernotifications/app-store-server-notifications-version-1), the following notification type and top-level objects are deprecated and removed: `RENEWAL,latest_receipt`, `latest_receipt_info`, `latest_expired_receipt`, and `latest_expired_receipt_info`. For more information, see [`responseBodyV1`](/documentation/appstoreservernotifications/responsebodyv1) and [`notification_type`](/documentation/appstoreservernotifications/notification_type).
    

### [November 21, 2019 - version 1](/documentation/AppStoreServerNotifications/app-store-server-notifications-changelog#November-21-2019-version-1)

**New features**

*   App Store Server Notifications is available.
    

## [See Also](/documentation/AppStoreServerNotifications/app-store-server-notifications-changelog#see-also)

### [Essentials](/documentation/AppStoreServerNotifications/app-store-server-notifications-changelog#Essentials)

[

Enabling App Store Server Notifications](/documentation/appstoreservernotifications/enabling-app-store-server-notifications)

Configure your server and provide an HTTPS URL to receive notifications about in-app purchase events and unreported external purchase tokens.

[

Receiving App Store Server Notifications](/documentation/appstoreservernotifications/receiving-app-store-server-notifications)

Implement server-side code to receive and parse notification posts.

[

Responding to App Store Server Notifications](/documentation/appstoreservernotifications/responding-to-app-store-server-notifications)

Send HTTP status codes to indicate the success of a notification post.