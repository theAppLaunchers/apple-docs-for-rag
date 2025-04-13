

- PassKit (Apple Pay and Wallet)
- PKPaymentRequestUpdate
-  deferredPaymentRequest 

Instance Property

# deferredPaymentRequest

The deferred payment request to update the payment request with.

iOS 16.4+iPadOS 16.4+Mac Catalyst 16.4+macOS 13.3+visionOS 1.0+

``` source
var deferredPaymentRequest: PKDeferredPaymentRequest? { get set }
```

## Discussion

The default value is `nil`, which indicates the request doesn’t require an update.

Warning

Changing the billingAgreement along with this property causes the framework to invalidate the current payment request, close the payment sheet, and return an error in the completion handler

You can’t use this property simultaneously with multitoken contexts, recurring payment requests, or automatic reload payment requests.

