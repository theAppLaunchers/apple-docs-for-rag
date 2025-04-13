

- PassKit (Apple Pay and Wallet)
- PKDeferredPaymentRequest
-  deferredBilling 

Instance Property

# deferredBilling

An object that contains details about the deferred payment.

iOS 16.4+iPadOS 16.4+Mac Catalyst 16.4+macOS 13.3+visionOS 1.0+

``` source
var deferredBilling: PKDeferredPaymentSummaryItem { get set }
```

## Discussion

For example “Pay \$2.99 on October 9, 2023.”

## See Also

### Setting payment summary items

class PKDeferredPaymentSummaryItem

An object that defines a summary item for a payment that occurs at a later date, such as a pre-order.

