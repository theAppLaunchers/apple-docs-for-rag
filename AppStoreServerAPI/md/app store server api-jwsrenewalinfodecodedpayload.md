

- App Store Server API
-  JWSRenewalInfoDecodedPayload 

Object

# JWSRenewalInfoDecodedPayload

A decoded payload containing subscription renewal information for an auto-renewable subscription.

App Store Server API 1.0+

``` source
object JWSRenewalInfoDecodedPayload
```

## Properties

`appAccountToken`

appAccountToken

A UUID you create at the time of purchase that associates the transaction with a customer on your own service. This is the token that applies to the upcoming renewal transaction. If your app doesn’t provide an `appAccountToken`, this field is omitted. For more information, see appAccountToken(_:).

`appTransactionId`

appTransactionId

The unique identifier of the app download transaction.

`autoRenewProductId`

autoRenewProductId

The identifier of the product that renews at the next billing period.

`autoRenewStatus`

autoRenewStatus

The renewal status of the auto-renewable subscription.

`currency`

currency

The currency code for the `renewalPrice` of the subscription.

`eligibleWinBackOfferIds`

eligibleWinBackOfferIds

The list of win-back offer IDs that the customer is eligible for.

`environment`

environment

The server environment, either sandbox or production.

`expirationIntent`

expirationIntent

The reason the subscription expired.

`gracePeriodExpiresDate`

gracePeriodExpiresDate

The time when the Billing Grace Period for subscription renewals expires.

`isInBillingRetryPeriod`

isInBillingRetryPeriod

A Boolean value that indicates whether the App Store is attempting to automatically renew the expired subscription.

`offerDiscountType`

offerDiscountType

The payment mode of the discount offer.

`offerIdentifier`

offerIdentifier

The offer code or the promotional offer identifier.

`offerPeriod`

offerPeriod

The duration of the offer.

`offerType`

offerType

The type of subscription offer.

`originalTransactionId`

originalTransactionId

The transaction identifier of the original purchase associated with this transaction.

`priceIncreaseStatus`

priceIncreaseStatus

The status that indicates whether the auto-renewable subscription is subject to a price increase.

`productId`

productId

The product identifier of the In-App Purchase.

`recentSubscriptionStartDate`

recentSubscriptionStartDate

The earliest start date of the auto-renewable subscription in a series of subscription purchases that ignores all lapses of paid service that are 60 days or fewer.

`renewalDate`

renewalDate

The UNIX time, in milliseconds, when the most recent auto-renewable subscription purchase expires.

`renewalPrice`

renewalPrice

The renewal price, in milliunits, of the auto-renewable subscription that renews at the next billing period.

`signedDate`

signedDate

The UNIX time, in milliseconds, that the App Store signed the JSON Web Signature (JWS) data.

`advancedCommerceInfo`

advancedCommerceRenewalInfo

Renewal information that is present only for Advanced Commerce SKUs.

## Mentioned in 

App Store Server API changelog

## See Also

### JWS headers and payloads

type JWSTransaction

Transaction information signed by the App Store, in JSON Web Signature (JWS) Compact Serialization format.

type JWSRenewalInfo

Subscription renewal information, signed by the App Store, in JSON Web Signature (JWS) format.

object JWSDecodedHeader

A decoded JSON Web Signature (JWS) header containing transaction or renewal information.

object JWSTransactionDecodedPayload

A decoded payload that contains transaction information.

Data types

Refer to these data types for decoded transaction and renewal information payloads.

