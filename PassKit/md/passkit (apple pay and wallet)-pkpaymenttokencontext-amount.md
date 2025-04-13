

- PassKit (Apple Pay and Wallet)
- PKPaymentTokenContext
-  amount 

Instance Property

# amount

The amount to authorize for the payment token.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+visionOS 1.0+

``` source
@NSCopying
var amount: NSDecimalNumber { get set }
```

## Discussion

The currency for the amount is the currency set in the enclosing payment request.

This amount must be less than or equal to the total of the enclosing payment request. The sum of all payment token contexts must be less than or equal to the grand total amount of the enclosing payment request that you provide in the last payment summary item. For more information, see PKPaymentSummaryItem.

