

- External Purchase Server API
-  eventType 

Type

# eventType

The type of transaction the line item reports, whether it’s a buy or refund.

External Purchase Server API 1.0.0+

``` source
string eventType
```

## Possible Values 

`BUY`  

`REFUND`  

## Mentioned in 

Reporting tokens with transactions

## Discussion

Allowed values: `BUY`, `REFUND`

The `eventType` field describes the type of transaction of the line item. Specify an `eventType` in the line item objects OneTimeBuyLineItem, SubscriptionBuyLineItem, and RefundLineItem.

Use the `eventType` values as follows:

- `BUY`: The line item describes a product purchase, such as a one-time buy, or a subscription event, including when there’s no charge, such as with a free trial. Use this value in the OneTimeBuyLineItem and SubscriptionBuyLineItem objects.

- `REFUND`: The line item describes a refund or chargeback, up to the full amount of the `BUY` transaction in the referenceLineItemId. Use this value in a RefundLineItem object.

## See Also

### Providing transaction info

type creationDate

The UNIX date, in milliseconds, that the customer authorized the transaction.

type referenceLineItemId

The line item identifier of another transaction, that the report references.

