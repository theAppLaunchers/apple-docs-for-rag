

- Apple Pay on the Web
- ApplePaySession
-  supportsVersion 

Type Method

# supportsVersion

Detects whether a web browser supports a particular Apple Pay version.

Safari Desktop 10.0+Safari Mobile 10.0+

``` source
static boolean supportsVersion();
```

## Parameters 

`version`  

An integer specifying the Apple Pay version number. For the best compatibility with operating systems and browsers, use the lowest possible version number that supports the features required. See Apple Pay on the web version history for version numbers and detailed information.

## Return Value

A Boolean value that indicates whether the web browser (Safari) supports a particular Apple Pay version. Returns `false` if the web browser does not support the specified version.

## Mentioned in 

Apple Pay on the Web Version 4 Release Notes

## Discussion

Apple increments the Apple Pay version number when adding new functionality that is not backward compatible with previous versions of Safari. The same Apple Pay version number applies to both Apple Pay JS and Payment Request APIs.

Check version support to ensure new API can run in the user’s browser, and provide fallback to earlier API versions whenever possible for broadest compatibility. See Apple Pay on the web version history for the version numbers and detailed information.

## See Also

### Determining support for API and payments

applePayCapabilities

Indicates whether the device supports Apple Pay and whether the person has an active card in Wallet that qualifies for web payments.

canMakePayments

Indicates whether the device supports Apple Pay.

canMakePaymentsWithActiveCard

Indicates whether the device supports Apple Pay and whether the user has an active card in Wallet.

Deprecated

