

- PassKit (Apple Pay and Wallet)
- PKPaymentRequest
-  supportedNetworks 

Instance Property

# supportedNetworks

The payment methods that you support.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 11.0+visionOS 1.0+watchOS 3.0+

``` source
var supportedNetworks: [PKPaymentNetwork] { get set }
```

## Discussion

This property constrains the payment methods that the user can select to fund the payment. For possible values, see PKPaymentNetwork.

In macOS 12.3, iOS 15.4, watchOS 8.5, and Mac Catalyst 15.4 or later, specify payment methods in the order you prefer. For example, to specify the default network to use for cobadged cards, set the first element in the array to the default network, and alternate networks afterward in the order you prefer.

Note

Apps supporting debit networks should check for regional regulations. For more information, see Complying with regional regulations.

## See Also

### Selecting the payment networks

class func availableNetworks() -> [PKPaymentNetwork]

Returns the list of available payment methods that Apple Pay supports.

struct PKPaymentNetwork

A type that represents a payment method.

