

- PassKit (Apple Pay and Wallet)
- PKDeferredPaymentRequest
-  freeCancellationDate 

Instance Property

# freeCancellationDate

The date before which you must cancel a deferred payment without incurring any cancellation charges.

iOS 16.4+iPadOS 16.4+Mac Catalyst 16.4+macOS 13.3+visionOS 1.0+

``` source
var freeCancellationDate: Date? { get set }
```

## Discussion

If you set freeCancellationDate, you need to set freeCancellationDateTimeZone as well.

## See Also

### Describing a deferred payment

var billingAgreement: String?

The localized billing agreement the framework displays to the user prior to payment authorization.

var paymentDescription: String

A description of the deferred payment.

var freeCancellationDateTimeZone: TimeZone?

The time zone at the destination location of the payment.

