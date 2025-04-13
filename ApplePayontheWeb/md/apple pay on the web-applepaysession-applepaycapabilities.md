

- Apple Pay on the Web
- ApplePaySession
-  applePayCapabilities 

Type Method

# applePayCapabilities

Indicates whether the device supports Apple Pay and whether the person has an active card in Wallet that qualifies for web payments.

Safari Desktop 10.0+Safari Mobile 10.0+

``` source
static Promise  applePayCapabilities(
 DOMString merchantIdentifier
);
```

## Parameters 

`merchantIdentifier`  

The ID the merchant creates when they enroll in Apple Pay.

## Return Value

Returns the PaymentCredentialStatus object.

## Mentioned in 

Checking for Apple Pay availability

## Discussion

Important

This method applies to Apple Pay JS API version `1.latest`.

This method asynchronously contacts the Apple Pay servers as part of the verification process. You can use this method to check for support on third-party browsers.

According to the Acceptable Use Guidelines for Apple Pay on the Web, if you invoke the `applePayCapabilities` method and determine that a person has an active card provisioned into Wallet, then Apple Pay should be the primary, but not necessarily sole, payment option on any webpage that accepts payments, like the checkout page or product detail page. In all other situations, use canMakePayments instead. For more information, see Checking for Apple Pay availability.

Note

Some cards, such as transit cards, are only enabled for POS payments and therefore won’t qualify for payments on the web.

The following code demonstrates calling this method with each of the possible return values, to determine when to display an Apple Pay button.

```
// Check if the Apple Pay JS API is available.
  if (window.ApplePaySession) {
    var merchantIdentifier = 'YOUR MERCHANT IDENTIFIER';
    var promise = ApplePaySession.applePayCapabilities(merchantIdentifier);
    promise.then(function(capabilities) {
      // Check whether the person has an active payment credential provisioned in Wallet.
      switch (capabilities.paymentCredentialStatus) {
        case "paymentCredentialsAvailable":
          // Display an Apple Pay button and offer Apple Pay as the primary payment option. 
        case "paymentCredentialStatusUnknown":
          // Display an Apple Pay button and offer Apple Pay as a payment option.
        case "paymentCredentialsUnavailable":
          // Consider displaying an Apple Pay button.
        case "applePayUnsupported":
          // Don't show an Apple Pay button or offer Apple Pay.
      }
    })
  }
```

## See Also

### Apple Pay availability

Checking for Apple Pay availability

Use the Apple Pay JS API to check whether Apple Pay is available, to check whether a device has a payment credential provisioned in Wallet, and to determine when to display an Apple Pay button.

canMakePayments

Indicates whether the device supports Apple Pay.

canMakePaymentsWithActiveCard

Indicates whether the device supports Apple Pay and whether the user has an active card in Wallet.

Deprecated

PaymentCredentialStatus

Information about whether the device supports Apple Pay and the possible payment credentials the person has provisioned in Wallet.

PaymentCredentialStatusResponse

The response for information about the device’s support for Apple Pay and the payment credential status.

