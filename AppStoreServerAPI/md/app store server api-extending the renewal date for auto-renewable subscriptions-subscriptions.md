

- App Store Server API
-  Extending the renewal date for auto-renewable subscriptions 

Article

# Extending the renewal date for auto-renewable subscriptions

Compensate eligible active subscribers for service interruptions by extending a subscription’s renewal date.

## Overview

If your service experiences a temporary outage, canceled event, or interruption to a live streamed event, you may choose to compensate your customers by extending the renewal date of their paid, active subscription. The App Store Server API provides two endpoints for requesting such extensions:

- Extend a Subscription Renewal Date for an individual subscription

- Extend Subscription Renewal Dates for All Active Subscribers for all subscriptions based on a product identifier, optionally limited to a list of storefronts

You can move the renewal date for active auto-renewable subscriptions up to 90 days into the future if your service experiences an unexpected outage. To give you flexibility to resolve service issues or outages, you can extend the renewal date twice within a year (365 days) per customer.

Note

After the subscription renewal extension goes into effect, there’s no way to reverse it. The extension period doesn’t count toward the one year of paid service when the App Store calculates the developer’s commission rate.

After a successful renewal date extension, Apple sends an email to notify the customer of their updated subscription renewal date.

### Determine eligible subscriptions

Only active auto-renewable subscriptions with at least one previously paid period are eligible to have a renewal date extension.

The following types of subscriptions aren’t eligible for renewal date extensions:

- Subscriptions in a free offer period

- Inactive subscriptions in a billing retry state

- Subscriptions in a billing grace period state with an expiration date in the past

- Subscriptions that have already received two renewal date extensions within the past 365 days

- Expired subscriptions

The App Store attempts to extend the renewal dates for eligible subscriptions only.

When the system extends eligible purchased subscriptions that support Family Sharing, it automatically extends the family members’ subscriptions as well. However, the Extend a Subscription Renewal Date endpoint doesn’t support requests to extend a family member’s subscription directly.

### Extend renewal dates for one or many subscribers

To request a renewal date extension for all eligible subscribers, call the Extend Subscription Renewal Dates for All Active Subscribers endpoint. You indicate the subscription by its productId. This endpoint is convenient for applying the renewal date extension to a large number of subscriptions with just one call. If a server outage affects some regions and not others, you can limit the request by storefront by including the optional `storefrontCountryCodes` property in the request body, MassExtendRenewalDateRequest.

To request a renewal date extension for a single subscriber, call the Extend a Subscription Renewal Date endpoint. You identify the subscription with an originalTransactionId. Use this endpoint to retry a renewal date extension that fails with the other endpoint, as the Retry attempts that fail section below describes.

### Receive in-progress and summary notifications

Requests to the Extend Subscription Renewal Dates for All Active Subscribers endpoint can take hours or days to complete, depending on the number of subscribers. The App Store server sends real-time notifications as it processes your request. The notifications inform you as each renewal date extension succeeds or fails, as well as when your request is complete.

To receive notifications, support App Store Server Notifications V2 on your server. For more information, see Enabling App Store Server Notifications.

The following table lists the notifications and their notificationType and subtype values:

| Notification type | Subtype | Description |
|----|----|----|
| `RENEWAL_EXTENDED` | (none) | The App Store extended the subscription renewal date for a specific subscription. |
| `RENEWAL_EXTENSION` | `FAILURE` | The subscription-renewal-date extension failed for a specific subscription. |
| `RENEWAL_EXTENSION` | `SUMMARY` | The request is complete. |

For more information about the contents of a notification payload, see responseBodyV2DecodedPayload.

For requests to the Extend a Subscription Renewal Date endpoint, App Store Server Notifications sends a `RENEWAL_EXTENDED` notification when the request succeeds. The endpoint returns more information in its response body, ExtendRenewalDateResponse.

### Check whether a request is complete

To check whether your request to Extend Subscription Renewal Dates for All Active Subscribers is complete, call the Get Status of Subscription Renewal Date Extensions endpoint. Complete requests include the final count of successful and failed renewal date extensions. If you don’t need this status on demand, use App Store Server Notifications for status information instead, as the previous section describes.

### Retry attempts that fail

The App Store server sends real-time notifications as it processes your request to Extend Subscription Renewal Dates for All Active Subscribers. The notifications inform you each time an attempt to extend the renewal date succeeds or fails. You can retry the failed attempts by calling the Extend a Subscription Renewal Date endpoint with the failed subscription’s transaction identifier. Follow these steps:

1.  Support App Store Server Notifications V2 on your server. For more information, see Enabling App Store Server Notifications.

2.  Look for notifications with a notificationType of `RENEWAL_EXTENSION` and subtype of `FAILURE`. The notification identifies a specific subscription that failed to receive a subscription-renewal-date extension.

3.  Find the subscription’s transaction identifier in the notification’s payload, responseBodyV2DecodedPayload. Specifically, use the `originalTransactionId` in the JWSTransactionDecodedPayload, which you get from the JWSTransaction of the data object in the payload.

4.  Call Extend a Subscription Renewal Date using the `originalTransactionID`.

## See Also

### Subscription-renewal-date extension

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

object MassExtendRenewalDateResponse

A response that indicates the server successfully received the subscription-renewal-date extension request.

object MassExtendRenewalDateStatusResponse

A response that indicates the current status of a request to extend the subscription renewal date to all eligible subscribers.

