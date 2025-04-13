

- App Store Server Notifications
-  notificationType 

Type

# notificationType

The type that describes the in-app purchase or external purchase event for which the App Store sends the version 2 notification.

App Store Server Notifications 2.0+

``` source
string notificationType
```

## Possible Values 

`CONSUMPTION_REQUEST`  

A notification type that indicates that the customer initiated a refund request for a consumable in-app purchase or auto-renewable subscription, and the App Store is requesting that you provide consumption data. For more information, see Send Consumption Information.

`DID_CHANGE_RENEWAL_PREF`  

A notification type that, along with its subtype, indicates that the customer made a change to their subscription plan. If the `subtype` is `UPGRADE`, the user upgraded their subscription. The upgrade goes into effect immediately, starting a new billing period, and the user receives a prorated refund for the unused portion of the previous period. If the `subtype` is `DOWNGRADE`, the customer downgraded their subscription. Downgrades take effect at the next renewal date and don’t affect the currently active plan.

If the `subtype` is empty, the user changed their renewal preference back to the current subscription, effectively canceling a downgrade.

For more information on subscription levels, see Ranking subscriptions within the group.

`DID_CHANGE_RENEWAL_STATUS`  

A notification type that, along with its subtype, indicates that the customer made a change to the subscription renewal status. If the `subtype` is `AUTO_RENEW_ENABLED`, the customer reenabled subscription auto-renewal. If the `subtype` is `AUTO_RENEW_DISABLED`, the customer disabled subscription auto-renewal, or the App Store disabled subscription auto-renewal after the customer requested a refund.

`DID_FAIL_TO_RENEW`  

A notification type that, along with its subtype, indicates that the subscription failed to renew due to a billing issue. The subscription enters the billing retry period. If the `subtype` is `GRACE_PERIOD`, continue to provide service through the grace period. If the `subtype` is empty, the subscription isn’t in a grace period and you can stop providing the subscription service.

Inform the customer that there may be an issue with their billing information. The App Store continues to retry billing for 60 days, or until the customer resolves their billing issue or cancels their subscription, whichever comes first. For more information, see Reducing Involuntary Subscriber Churn.

`DID_RENEW`  

A notification type that, along with its subtype, indicates that the subscription successfully renewed. If the `subtype` is `BILLING_RECOVERY`, the expired subscription that previously failed to renew has successfully renewed. If the `subtype` is empty, the active subscription has successfully auto-renewed for a new transaction period. Provide the customer with access to the subscription’s content or service.

`EXPIRED`  

A notification type that, along with its subtype, indicates that a subscription expired. If the `subtype` is `VOLUNTARY`, the subscription expired after the user disabled subscription renewal. If the `subtype` is `BILLING_RETRY`, the subscription expired because the billing retry period ended without a successful billing transaction. If the `subtype` is `PRICE_INCREASE`, the subscription expired because the customer didn’t consent to a price increase that requires customer consent. If the `subtype` is `PRODUCT_NOT_FOR_SALE`, the subscription expired because the product wasn’t available for purchase at the time the subscription attempted to renew.

A notification without a subtype indicates that the subscription expired for some other reason.

`EXTERNAL_PURCHASE_TOKEN`  

A notification type that, along with its subtype UNREPORTED, indicates that Apple created an external purchase token for your app, but didn’t receive a report. For more information about reporting the token, see externalPurchaseToken.

This notification applies only to apps that use the External Purchase to provide alternative payment options.

`GRACE_PERIOD_EXPIRED`  

A notification type that indicates that the billing grace period has ended without renewing the subscription, so you can turn off access to the service or content. Inform the customer that there may be an issue with their billing information. The App Store continues to retry billing for 60 days, or until the customer resolves their billing issue or cancels their subscription, whichever comes first. For more information, see Reducing Involuntary Subscriber Churn.

`METADATA_UPDATE`  

A notification type that indicates you used the Change Subscription Metadata endpoint to change the metadata for a subscription. This notification only applies to apps that use the Advanced Commerce API.

`MIGRATION`  

A notification type that indicates you used the Migrate a Subscription to Advanced Commerce API endpoint. This notification only applies to apps that use the Advanced Commerce API.

`OFFER_REDEEMED`  

A notification type that, along with its subtype, indicates that a customer with an active subscription redeemed a subscription offer.

If the `subtype` is `UPGRADE`, the customer redeemed an offer to upgrade their active subscription, which goes into effect immediately. If the subtype is `DOWNGRADE`, the customer redeemed an offer to downgrade their active subscription, which goes into effect at the next renewal date. If the customer redeemed an offer for their active subscription, you receive an `OFFER_REDEEMED` notification type without a `subtype`.

For more information about subscription offer codes, see Supporting subscription offer codes in your app. For more information about promotional offers, see Implementing promotional offers in your app.

`ONE_TIME_CHARGE`  

The `ONE_TIME_CHARGE` notification is currently available only in the sandbox environment.

A notification type that indicates the customer purchased a consumable, non-consumable, or non-renewing subscription. The App Store also sends this notification when the customer receives access to a non-consumable product through Family Sharing.

For notifications about auto-renewable subscription purchases, see the `SUBSCRIBED` notification type.

`PRICE_CHANGE`  

A notification type that indicates that you called the Change Subscription Price endpoint. This notification only applies to apps that use the Advanced Commerce API.

`PRICE_INCREASE`  

A notification type that, along with its subtype, indicates that the system has informed the customer of an auto-renewable subscription price increase.

If the price increase requires customer consent, the `subtype` is `PENDING` if the customer hasn’t responded to the price increase, or `ACCEPTED` if the customer has consented to the price increase.

If the price increase doesn’t require customer consent, the `subtype` is `ACCEPTED`.

For information about how the system calls your app before it displays the price consent sheet for subscription price increases that require customer consent, see paymentQueueShouldShowPriceConsent(_:). For information about managing subscription prices, see Managing Price Increases for Auto-Renewable Subscriptions and Managing Prices.

`REFUND`  

A notification type that indicates that the App Store successfully refunded a transaction for a consumable in-app purchase, a non-consumable in-app purchase, an auto-renewable subscription, or a non-renewing subscription.

The revocationDate contains the timestamp of the refunded transaction. The originalTransactionId and productId identify the original transaction and product. The revocationReason contains the reason.

To request a list of all refunded transactions for a customer, see Get Refund History in the App Store Server API.

`REFUND_DECLINED`  

A notification type that indicates the App Store declined a refund request.

`REFUND_REVERSED`  

A notification type that indicates the App Store reversed a previously granted refund due to a dispute that the customer raised. If your app revoked content or services as a result of the related refund, it needs to reinstate them.

This notification type can apply to any in-app purchase type: consumable, non-consumable, non-renewing subscription, and auto-renewable subscription. For auto-renewable subscriptions, the renewal date remains unchanged when the App Store reverses a refund.

`RENEWAL_EXTENDED`  

A notification type that indicates the App Store extended the subscription renewal date for a specific subscription. You request subscription-renewal-date extensions by calling Extend a Subscription Renewal Date or Extend Subscription Renewal Dates for All Active Subscribers in the App Store Server API.

`RENEWAL_EXTENSION`  

A notification type that, along with its subtype, indicates that the App Store is attempting to extend the subscription renewal date that you request by calling Extend Subscription Renewal Dates for All Active Subscribers.

If the subtype is `SUMMARY`, the App Store completed extending the renewal date for all eligible subscribers. See the summary in the responseBodyV2DecodedPayload for details. If the subtype is `FAILURE`, the renewal date extension didn’t succeed for a specific subscription. See the data in the responseBodyV2DecodedPayload for details.

`REVOKE`  

A notification type that indicates that an in-app purchase the customer was entitled to through Family Sharing is no longer available through sharing. The App Store sends this notification when a purchaser disables Family Sharing for their purchase, the purchaser (or family member) leaves the family group, or the purchaser receives a refund. Your app also receives a paymentQueue(\_:didRevokeEntitlementsForProductIdentifiers:) call. Family Sharing applies to non-consumable in-app purchases and auto-renewable subscriptions. For more information about Family Sharing, see Supporting Family Sharing in your app.

`SUBSCRIBED`  

A notification type that, along with its subtype, indicates that the customer subscribed to an auto-renewable subscription. If the subtype is `INITIAL_BUY`, the customer either purchased or received access through Family Sharing to the subscription for the first time. If the subtype is `RESUBSCRIBE`, the user resubscribed or received access through Family Sharing to the same subscription or to another subscription within the same subscription group.

For notifications about other product type purchases, see the `ONE_TIME_CHARGE` notification type.

`TEST`  

A notification type that the App Store server sends when you request it by calling the Request a Test Notification endpoint. Call that endpoint to test whether your server is receiving notifications. You receive this notification only at your request. For troubleshooting information, see the Get Test Notification Status endpoint.

## Mentioned in 

App Store Server Notifications changelog

Enabling App Store Server Notifications

## Discussion

The `notificationType appears` in the notification payload, responseBodyV2DecodedPayload. It describes the event that leads to the notification. Some notifications also have a subtype that further describes the event. See the responseBodyV2DecodedPayload for more information about the notification in the data, summary, or externalPurchaseToken object.

### Handle use cases for in-app purchase life-cycle events

When events occur that affect the customer’s in-app purchase and subscription life cycle, the App Store server sends you notifications. The following tables list the notifications by life-cycle events.

Events that enable service for a consumable, non-consumable, or non-renewing subscription in-app purchase result in the following notifications, currently available in the sandbox environment only:

| Event | Notification type | Notification subtype |
|----|----|----|
| Customer purchases a consumable, non-consumable, or non-renewing subscription. | `ONE_TIME_CHARGE` |  |
| Customer receives access to a non-consumable in-app purchase through Family Sharing. | `ONE_TIME_CHARGE` |  |

Events that enable service for subscriptions, including initial subscriptions, resubscribing, and successful auto-renewals, result in the following notifications:

| Event | Notification type | Notification subtype |
|----|----|----|
| Customer subscribes for the first time to any subscription within a subscription group. | `SUBSCRIBED` | `INITIAL_BUY` |
| Customer resubscribes to any subscription from the same subscription group as their expired subscription. | `SUBSCRIBED` | `RESUBSCRIBE` |
| The subscription successfully auto-renews. | `DID_RENEW` |  |
| A family member gains access to the subscription through Family Sharing after the purchaser subscribes for the first time. | `SUBSCRIBED` | `INITIAL_BUY` |
| A family member gains access to the subscription through Family Sharing after the purchaser resubscribes. | `SUBSCRIBED` | `RESUBSCRIBE` |

Customers changing their subscription options, including upgrading, downgrading, or canceling, result in the following notifications:

| Event | Notification type | Notification subtype |
|----|----|----|
| Customer downgrades a subscription within the same subscription group. | `DID_CHANGE_RENEWAL_PREF` | `DOWNGRADE` |
| Customer reverts to the previous subscription, effectively canceling their downgrade. | `DID_CHANGE_RENEWAL_PREF` |  |
| Customer upgrades a subscription within the same subscription group. | `DID_CHANGE_RENEWAL_PREF` | `UPGRADE` |
| Customer cancels the subscription from the App Store Subscriptions settings page. | `DID_CHANGE_RENEWAL_STATUS` | `AUTO_RENEW_DISABLED` |
| Customer subscribes again after canceling a subscription, which reenables auto-renew. | `DID_CHANGE_RENEWAL_STATUS` | `AUTO_RENEW_ENABLED` |
| The system disabled auto-renew because the customer initiated a refund through your app using the refund request API. | `DID_CHANGE_RENEWAL_STATUS` | `AUTO_RENEW_DISABLED` |

Customers redeeming subscription offers, such as promotional offers, offer codes, or win-back offers, result in the following notifications:

| Event | Notification type | Notification subtype |
|----|----|----|
| Customer redeems a promotional offer or offer code for an active subscription. | `OFFER_REDEEMED` |  |
| Customer redeems an offer code to subscribe for the first time. | `SUBSCRIBED` | `INITIAL_BUY` |
| Customer redeems a promotional offer, offer code, or win-back offer after their subscription expired. | `SUBSCRIBED` | `RESUBSCRIBE` |
| Customer redeems a promotional offer or offer code to upgrade their subscription. | `OFFER_REDEEMED` | `UPGRADE` |
| Customer redeems a promotional offer and downgrades their subscription. | `OFFER_REDEEMED` | `DOWNGRADE` |

Billing events, including billing retries, entering and exiting the billing grace period, and expiring subscriptions, result in the following notifications:

| Event | Notification type | Notification subtype |
|----|----|----|
| The subscription expires because the customer chose to cancel it. | `EXPIRED` | `VOLUNTARY` |
| The subscription expires because the developer removed the subscription from sale and the renewal fails. | `EXPIRED` | `PRODUCT_NOT_FOR_SALE` |
| The subscription expires because the billing retry period ends without recovering the subscription. | `EXPIRED` | `BILLING_RETRY` |
| The subscription fails to renew and enters the billing retry period. | `DID_FAIL_TO_RENEW` |  |
| The subscription fails to renew and enters the billing retry period with Billing Grace Period enabled. | `DID_FAIL_TO_RENEW` | `GRACE_PERIOD` |
| The billing retry successfully recovers the subscription. | `DID_RENEW` | `BILLING_RECOVERY` |
| The subscription exits the billing grace period (and continues in billing retry). | `GRACE_PERIOD_EXPIRED` |  |

Events or notifications that occur when you increase the price of an auto-renewable subscription include:

| Event | Notification type | Notification subtype |
|----|----|----|
| The system informs the customer of the auto-renewable subscription price increase that requires customer consent, and the customer doesn’t respond. | `PRICE_INCREASE` | `PENDING` |
| The auto-renewable subscription expires because the customer didn’t consent to the price increase that requires consent. | `EXPIRED` | `PRICE_INCREASE` |
| Customer consents to an auto-renewable subscription price increase that requires consent. | `PRICE_INCREASE` | `ACCEPTED` |
| The system notifies the customer of the auto-renewable subscription price increase that doesn’t require customer consent. | `PRICE_INCREASE` | `ACCEPTED` |
| Customer canceled the subscription after receiving a price increase notice or a request to consent to a price increase. | `DID_CHANGE_RENEWAL_STATUS` |  |

Customers requesting refunds or canceling Family Sharing result in the following notifications:

| Event | Notification type | Notification subtype |
|----|----|----|
| Apple refunds the transaction for a consumable or non-consumable in-app purchase, a non-renewing subscription, or an auto-renewable subscription. | `REFUND` |  |
| Apple reverses a previously granted refund due to a dispute that the customer raised. | `REFUND_REVERSED` |  |
| Apple declines a refund that the customer initiated in the app, using the request refund API. | `REFUND_DECLINED` |  |
| Apple requests consumption information for a refund request that a customer initiates. | `CONSUMPTION_REQUEST` |  |
| A family member loses access to the subscription through Family Sharing. | `REVOKE` |  |

Developers requesting subscription-renewal-date extensions result in the following notifications:

| Event | Notification type | Notification subtype |
|----|----|----|
| The App Store successfully extends a subscription renewal date for a specific subscription. | `RENEWAL_EXTENDED` |  |
| The App Store successfully completes extending the subscription renewal date for all eligible subscribers. | `RENEWAL_EXTENSION` | `SUMMARY` |
| The App Store failed to extend the subscription renewal date for a specific subscriber. | `RENEWAL_EXTENSION` | `FAILURE` |

## See Also

### Server notifications version 2

App Store Server Notifications V2

Specify your secure server’s URL in App Store Connect to receive version 2 notifications.

object responseBodyV2

The response body the App Store sends in a version 2 server notification.

object responseBodyV2DecodedPayload

A decoded payload that contains the version 2 notification data.

type subtype

A string that provides details about select notification types in version 2.

