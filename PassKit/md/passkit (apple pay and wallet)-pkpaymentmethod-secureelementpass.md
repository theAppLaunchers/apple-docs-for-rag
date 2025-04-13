

- PassKit (Apple Pay and Wallet)
- PKPaymentMethod
-  secureElementPass 

Instance Property

# secureElementPass

The accompanying Secure Element pass.

iOS 13.4+iPadOS 13.4+Mac Catalyst 13.4+macOS 11.0+visionOS 1.0+watchOS 6.2+

``` source
@NSCopying
var secureElementPass: PKSecureElementPass? { get }
```

## Discussion

If your app has an association with the pass that is funding the payment, this property contains information about that pass; otherwise, it’s `nil`.

Use this property to detect your brand of credit and debit cards. For example, you can provide a discount if the user pays using your store-branded credit card.

Note

To be able to access the pass, the issuer must add your App ID to the pass when it provisions it. To add your App ID to these passes, contact the bank that issues your cards or the person who manages your cobrand program.

## See Also

### Getting the pass

var paymentPass: PKPaymentPass?

The accompanying payment pass.

Deprecated

