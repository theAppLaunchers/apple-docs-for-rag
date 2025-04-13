

- App Store Server API
-  eligibleWinBackOfferIds 

Type

# eligibleWinBackOfferIds

An array of win-back offer identifiers that a customer is eligible to redeem, which sorts the identifiers with the best offers first.

App Store Server API 1.13+

``` source
[offerIdentifier] eligibleWinBackOfferIds
```

## Mentioned in 

App Store Server API changelog

## Discussion

Use this list to select an eligible win-back offer for a customer. The array contains strings that represent offer identifiers for win-back offers. You provide the offer identifier in App Store Connect when you configure a win-back offer.

The App Store sets the order of the eligible win-back offer IDs for each customer, with the best offer first. The order takes into account the available offers you configure in App Store Connect for the customer’s most recent subscription in the subscription group. Subscriptions in a Billing Grace Period or billing retry state aren’t eligible for win-back offers.

Win-back offers have a direct link. App Store Connect generates and displays the direct link when you configure the win-back offer. Use the direct link to merchandise the win-back offer through your own channels. For more information, see Supporting win-back offers in your app.

This array appears in a JWSTransactionDecodedPayload.

For information about configuring win-back offers in App Store Connect, see Set up win-back offers.

## See Also

### Subscription offers

type offerIdentifier

The string identifier of a subscription offer that you create in App Store Connect.

type offerPeriod

The duration of the offer.

type offerType

The type of subscription offer.

type offerDiscountType

The payment mode for subscription offers on an auto-renewable subscription.

