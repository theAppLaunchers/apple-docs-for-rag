*   [PassKit (Apple Pay and Wallet)](/documentation/passkit)
*   PKRecurringPaymentSummaryItem

Class

# PKRecurringPaymentSummaryItem

An object that defines a summary item for a payment that occurs repeatedly at a specified interval, such as a subscription.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+visionOS 1.0+watchOS 8.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class PKRecurringPaymentSummaryItem
```
```
```
```
```
```
```
```

## [Overview](/documentation/PassKit/PKRecurringPaymentSummaryItem#overview)

[`PKRecurringPaymentSummaryItem`](/documentation/passkit/pkrecurringpaymentsummaryitem) is a subclass of [`PKPaymentSummaryItemType`](/documentation/passkit/pkpaymentsummaryitemtype) and inherits all properties of the parent class.

Add a summary item of this type to the [`paymentSummaryItems`](/documentation/passkit/pkpaymentrequest/paymentsummaryitems) property of a [`PKPaymentRequest`](/documentation/passkit/pkpaymentrequest) to display to the user a recurring payment in the summary items on the payment sheet.

To describe a recurring payment, set the summary item values as follows:

*   In the [`amount`](/documentation/passkit/pkpaymentsummaryitem/amount) property, provide the billing amount for the set interval, for example, the amount charged per week if the [`intervalUnit`](/documentation/passkit/pkrecurringpaymentsummaryitem/intervalunit) is a week.
    
*   Omit the [`type`](/documentation/passkit/pkpaymentsummaryitem/type) property. The summary item type is only relevant for the [`PKPaymentSummaryItem`](/documentation/passkit/pkpaymentsummaryitem) parent class.
    
*   Set the [`startDate`](/documentation/passkit/pkrecurringpaymentsummaryitem/startdate) and [`endDate`](/documentation/passkit/pkrecurringpaymentsummaryitem/enddate) to represent the term for the recurring payments, as appropriate.
    
*   Set the [`intervalUnit`](/documentation/passkit/pkrecurringpaymentsummaryitem/intervalunit), [`intervalCount`](/documentation/passkit/pkrecurringpaymentsummaryitem/intervalcount), and [`endDate`](/documentation/passkit/pkrecurringpaymentsummaryitem/enddate) to specify a number of repeating payments.
    

For example, the following code shows a summary item that specifies six monthly payments that start on the transaction date:

```swift
```swift
```swift
```swift
```swift
```swift
let recurringPayment = PKRecurringPaymentSummaryItem(label: "Total Payment",                                                  NSDecimalNumber(string: "199.99"))
```
```
// Payment starts today.
recurringPayment.startDate = nil
// Pay once a month.
recurringPayment.intervalUnit = .month
recurringPayment.intervalCount = 1
// Make 5 more payments for a total of 6 payments.
```swift
```swift
var dateComponent = DateComponents()
```
```
dateComponent.month = 5
recurringPayment.endDate = Calendar.current.date(byAdding: dateComponent, Date())
```
```
```
```

The payment interval is a combination of the [`intervalUnit`](/documentation/passkit/pkrecurringpaymentsummaryitem/intervalunit) and the [`intervalCount`](/documentation/passkit/pkrecurringpaymentsummaryitem/intervalcount). For example, if you set the [`intervalUnit`](/documentation/passkit/pkrecurringpaymentsummaryitem/intervalunit) to .[`month`](/documentation/CoreFoundation/CFCalendarUnit/month) and [`intervalCount`](/documentation/passkit/pkrecurringpaymentsummaryitem/intervalcount) to `3`, then the payment interval is three months.

## [Topics](/documentation/PassKit/PKRecurringPaymentSummaryItem#topics)

### [Setting the payment period](/documentation/PassKit/PKRecurringPaymentSummaryItem#Setting-the-payment-period)

```swift
```swift
```swift
```swift
var startDate: Date?
```
```

The date of the first payment.
```
```swift
```swift
```swift
var endDate: Date?
```
```

The date of the final payment.
```
```

### [Setting the payment interval](/documentation/PassKit/PKRecurringPaymentSummaryItem#Setting-the-payment-interval)

```swift
```swift
```swift
```swift
var intervalUnit: NSCalendar.Unit
```
```

The amount of time – in calendar units such as day, month, or year – that represents a fraction of the total payment interval.
```
```swift
```swift
```swift
var intervalCount: Int
```
```

The number of interval units that make up the total payment interval.
```
```

## [Relationships](/documentation/PassKit/PKRecurringPaymentSummaryItem#relationships)

### [Inherits From](/documentation/PassKit/PKRecurringPaymentSummaryItem#inherits-from)

*   [`PKPaymentSummaryItem`](/documentation/passkit/pkpaymentsummaryitem)

### [Conforms To](/documentation/PassKit/PKRecurringPaymentSummaryItem#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)

## [See Also](/documentation/PassKit/PKRecurringPaymentSummaryItem#see-also)

### [Setting the payment summary items](/documentation/PassKit/PKRecurringPaymentSummaryItem#Setting-the-payment-summary-items)

```swift
```swift
```swift
```swift
var paymentSummaryItems: [PKPaymentSummaryItem]
```
```

An array of payment summary item objects that summarize the amount of the payment.
```
```swift
```swift
```swift
class PKPaymentSummaryItem
```
```

An object that defines a summary item in a payment request, taxes, discounts, shipping, a grand total, and the like.
```
```swift
```swift
```swift
class PKDeferredPaymentSummaryItem
```
```

An object that defines a summary item for a payment that occurs at a later date, such as a pre-order.
```
```