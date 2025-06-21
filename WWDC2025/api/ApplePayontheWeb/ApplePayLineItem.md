*   [Apple Pay on the Web](/documentation/applepayontheweb)
*   ApplePayLineItem

Structure

# ApplePayLineItem

A line item in a payment request—for example, total, tax, discount, or grand total.

Safari Desktop 10.0+Safari Mobile 10.0+

```swift
```swift
```swift
```swift
```swift
```swift
```

```
dictionary ApplePayLineItem {
	[`ApplePayLineItemType`](/documentation/applepayontheweb/applepaylineitemtype) type;
	DOMString label;
	DOMString amount;
	[`ApplePayPaymentTiming`](/documentation/applepayontheweb/applepaypaymenttiming) paymentTiming;
	Date recurringPaymentStartDate;
	[`ApplePayRecurringPaymentDateUnit`](/documentation/applepayontheweb/applepayrecurringpaymentdateunit) recurringPaymentIntervalUnit;
	long recurringPaymentIntervalCount;
	Date recurringPaymentEndDate;
	Date deferredPaymentDate;
	DOMString automaticReloadPaymentThresholdAmount;
};
```

```
```
```
```
```
```
```

## [Overview](/documentation/ApplePayontheWeb/ApplePayLineItem#overview)

Line items appear in the payment sheet.

The following code is an example of a line item for a $20 charge that recurs every six months starting on 01/01/2022 and ending on 01/01/2024:

```

```
{
    "label": "Subscription",
    "amount": "20.00",
    "type": "final",
    "paymentTiming": "recurring",
    "recurringPaymentStartDate": new Date("2022-01-01T00:00:00"),
    "recurringPaymentIntervalUnit": "month",
    "recurringPaymentIntervalCount": 6,
    "recurringPaymentEndDate": new Date("2024-01-01T00:00:00"),
}
```

```

The following code is an example of a line item for a deferred charge of $50 on 07/01/2023:

```

```
{
    "label": "After Trial Period",
    "amount": "50.00",
    "type": "final",
    "paymentTiming": "deferred",
    "deferredPaymentDate": new Date("2023-07-01T00:00:00"),
}
```

```

For examples of line items within an [`ApplePayPaymentRequest`](/documentation/applepayontheweb/applepaypaymentrequest), see [`lineItems`](/documentation/applepayontheweb/applepaypaymentrequest/lineitems) and [`total`](/documentation/applepayontheweb/applepaypaymentrequest/total).

## [Topics](/documentation/ApplePayontheWeb/ApplePayLineItem#topics)

### [Setting line item properties](/documentation/ApplePayontheWeb/ApplePayLineItem#Setting-line-item-properties)

[`label`](/documentation/applepayontheweb/applepaylineitem/label)

A required value that’s a short, localized description of the line item.

[`amount`](/documentation/applepayontheweb/applepaylineitem/amount)

A required value that’s the monetary amount of the line item.

[`type`](/documentation/applepayontheweb/applepaylineitem/type)

A value that indicates whether the line item is final or pending.

[`ApplePayLineItemType`](/documentation/applepayontheweb/applepaylineitemtype)

A type that indicates whether a line item is final or pending.

### [Configuring payment timing](/documentation/ApplePayontheWeb/ApplePayLineItem#Configuring-payment-timing)

[`paymentTiming`](/documentation/applepayontheweb/applepaylineitem/paymenttiming)

The time that the payment occurs as part of a successful transaction.

[`ApplePayPaymentTiming`](/documentation/applepayontheweb/applepaypaymenttiming)

A type that indicates the time a payment occurs in a transaction.

### [Configuring recurring payments](/documentation/ApplePayontheWeb/ApplePayLineItem#Configuring-recurring-payments)

[`recurringPaymentStartDate`](/documentation/applepayontheweb/applepaylineitem/recurringpaymentstartdate)

The date of the first payment.

[`recurringPaymentEndDate`](/documentation/applepayontheweb/applepaylineitem/recurringpaymentenddate)

The date of the final payment.

[`recurringPaymentIntervalUnit`](/documentation/applepayontheweb/applepaylineitem/recurringpaymentintervalunit)

The amount of time — in calendar units, such as day, month, or year — that represents a fraction of the total payment interval.

[`recurringPaymentIntervalCount`](/documentation/applepayontheweb/applepaylineitem/recurringpaymentintervalcount)

The number of interval units that make up the total payment interval.

[`ApplePayRecurringPaymentDateUnit`](/documentation/applepayontheweb/applepayrecurringpaymentdateunit)

A type that indicates calendrical units, such as year, month, day, and hour.

### [Configuring deferred payments](/documentation/ApplePayontheWeb/ApplePayLineItem#Configuring-deferred-payments)

[`deferredPaymentDate`](/documentation/applepayontheweb/applepaylineitem/deferredpaymentdate)

The date, in the future, of the payment.

### [Configuring automatic reload payments](/documentation/ApplePayontheWeb/ApplePayLineItem#Configuring-automatic-reload-payments)

[`automaticReloadPaymentThresholdAmount`](/documentation/applepayontheweb/applepaylineitem/automaticreloadpaymentthresholdamount)

The balance an account reaches before the merchant applies the automatic reload amount.

## [See Also](/documentation/ApplePayontheWeb/ApplePayLineItem#see-also)

### [Setting the total and summary line items](/documentation/ApplePayontheWeb/ApplePayLineItem#Setting-the-total-and-summary-line-items)

[`total`](/documentation/applepayontheweb/applepaypaymentrequest/total)

A line item that represents the total for the payment.

[`lineItems`](/documentation/applepayontheweb/applepaypaymentrequest/lineitems)

A set of line items that explain recurring payments and additional charges and discounts.

[`ApplePayLineItemType`](/documentation/applepayontheweb/applepaylineitemtype)

A type that indicates whether a line item is final or pending.