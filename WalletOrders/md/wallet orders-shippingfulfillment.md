

- Wallet Orders
-  ShippingFulfillment 

Object

# ShippingFulfillment

The details of a shipped order.

iOS 16.0+iPadOS 16.0+macOS 13.0+

``` source
object ShippingFulfillment
```

## Properties

`fulfillmentIdentifier`

`string`

 (Required) 

An opaque value that uniquely identifies this fulfillment in the order. This isn’t displayed to the user, and is only used for determining changes and user notifications.

`fulfillmentType`

`string`

 (Required) 

The type of fulfillment, which is `shipping`.

Value: `shipping`

`status`

`string`

 (Required) 

The status of the fulfillment.

Possible Values: `open, processing, onTheWay, outForDelivery, delivered, shipped, issue, cancelled`

`carrier`

`string`

The shipping carrier used to complete this fulfillment.

`deliveredAt`

`date-time`

The date and time when the carrier delivered the shipment, in RFC 3339 format.

`estimatedDeliveryAt`

`date-time`

The estimated delivery date and time from the carrier, in RFC 3339 format. The system ignores the time components unless the carrier provides a window duration.

`estimatedDeliveryWindowDuration`

`duration`

The duration for the estimated delivery window, in ISO 8601-1 duration format.

`lineItems`

`[`LineItem`]`

The items the carrier will ship, displayed in the order provided.

`notes`

`string`

Additional localized information about the shipment. For example, whether it requires a signature.

`recipient`

ShippingFulfillment.Recipient

The recipient of the shipment.

`shippedAt`

`date-time`

The date and time when the carrier shipped the order, in RFC 3339 format.

`shippingType`

`string`

The type used for display.

Default: shipping

Possible Values: `shipping, delivery`

`statusDescription`

`string`

A localized message describing the fulfillment status.

`trackingNumber`

`string`

The tracking number provided by the shipping carrier.

`trackingURL`

`uri`

A URL where the customer can track the shipment.

## Attributes 

Possible types:

## Topics

### Objects

object ShippingFulfillment.Recipient

The recipient of the shipment.

## See Also

### Supporting objects

object Customer

The details of the order’s customer.

object Merchant

The merchant associated with the order.

object Address

The physical address for an order.

object Application

The details of an app in the App Store.

object Barcode

The details of a barcode for an order.

object CurrencyAmount

An amount of money.

object LineItem

An item associated with the order.

object Location

A geographic location.

object OrderIdentifiers

The unique identifiers associated with orders.

object OrderProvider

Information about the platform providing the order data.

object Payment

The payment information associated with the order.

object Payment.SummaryItems

A breakdown of the total payment.

object PaymentMethod

The payment method for the transaction.

object PaymentTransaction

The details about a payment transaction.

object PickupFulfillment

The details of a pickup order.

