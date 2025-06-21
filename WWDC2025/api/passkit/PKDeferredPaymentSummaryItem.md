*   [PassKit (Apple Pay and Wallet)](/documentation/passkit)
*   PKDeferredPaymentSummaryItem

Class

# PKDeferredPaymentSummaryItem

An object that defines a summary item for a payment that occurs at a later date, such as a pre-order.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+visionOS 1.0+watchOS 8.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class PKDeferredPaymentSummaryItem
```
```
```
```
```
```
```
```

## [Topics](/documentation/PassKit/PKDeferredPaymentSummaryItem#topics)

### [Setting the payment date](/documentation/PassKit/PKDeferredPaymentSummaryItem#Setting-the-payment-date)

```swift
```swift
```swift
```swift
var deferredDate: Date
```
```

The date, in the future, of the payment.
```
```

## [Relationships](/documentation/PassKit/PKDeferredPaymentSummaryItem#relationships)

### [Inherits From](/documentation/PassKit/PKDeferredPaymentSummaryItem#inherits-from)

*   [`PKPaymentSummaryItem`](/documentation/passkit/pkpaymentsummaryitem)

### [Conforms To](/documentation/PassKit/PKDeferredPaymentSummaryItem#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)

## [See Also](/documentation/PassKit/PKDeferredPaymentSummaryItem#see-also)

### [Setting payment summary items](/documentation/PassKit/PKDeferredPaymentSummaryItem#Setting-payment-summary-items)

```swift
```swift
```swift
```swift
var deferredBilling: PKDeferredPaymentSummaryItem
```
```

An object that contains details about the deferred payment.
```
```