

- App Store Server API
-  MassExtendRenewalDateResponse 

Object

# MassExtendRenewalDateResponse

A response that indicates the server successfully received the subscription-renewal-date extension request.

App Store Server API 1.7+

``` source
object MassExtendRenewalDateResponse
```

## Properties

`requestIdentifier`

requestIdentifier

A string that contains the `UUID` that identifies the subscription-renewal-date extension request.

Maximum length: `128`

## Mentioned in 

App Store Server API changelog

## Discussion

The App Store server returns this response when you call the Extend Subscription Renewal Dates for All Active Subscribers endpoint. Because the endpoint runs asynchronously, this response means the App Store received your request and is processing it. The request may take multiple hours or days to complete, depending on the number of subscribers.

As the App Store server processes your request, it sends notifications (App Store Server Notifications V2) in near real-time to report on each subscription it processes. Look for notifications with the notificationType of `RENEWAL_EXTENSION` and `RENEWAL_EXTENDED`. The server sends a `RENEWAL_EXTENSION` notification with a subtype of `SUCCESS` when it completes the request.

The Get Status of Subscription Renewal Date Extensions endpoint reports on whether your request is complete. For completed requests, it also reports the count of successful and failed subscription-renewal-date extensions.

For more information, see Extending the renewal date for auto-renewable subscriptions.

## See Also

### Subscription-renewal-date extension

Extending the renewal date for auto-renewable subscriptions

Compensate eligible active subscribers for service interruptions by extending a subscription’s renewal date.

Extend a Subscription Renewal Date

Extends the renewal date of a customer’s active subscription using the original transaction identifier.

Extend Subscription Renewal Dates for All Active Subscribers

Uses a subscription’s product identifier to extend the renewal date for all of its eligible active subscribers.

Get Status of Subscription Renewal Date Extensions

Checks whether a renewal date extension request completed, and provides the final count of successful or failed extensions.

object ExtendRenewalDateRequest

The request body that contains subscription-renewal-extension data for an individual subscription.

object ExtendRenewalDateResponse

A response that indicates whether an individual renewal-date extension succeeded, and related details.

object MassExtendRenewalDateRequest

The request body that contains subscription-renewal-extension data to apply for all eligible active subscribers.

object MassExtendRenewalDateStatusResponse

A response that indicates the current status of a request to extend the subscription renewal date to all eligible subscribers.

