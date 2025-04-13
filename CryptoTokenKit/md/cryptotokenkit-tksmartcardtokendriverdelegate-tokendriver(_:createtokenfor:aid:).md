

- CryptoTokenKit
- TKSmartCardTokenDriverDelegate
-  tokenDriver(\_:createTokenFor:aid:) 

Instance Method

# tokenDriver(\_:createTokenFor:aid:)

Tells the delegate that a new Smart Card is detected.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.12+tvOS 11.0+visionOS 1.0+watchOS 4.0+

``` source
func tokenDriver(
    _ driver: TKSmartCardTokenDriver,
    createTokenFor smartCard: TKSmartCard,
    aid AID: Data?
) throws -> TKSmartCardToken
```

**Required**

## Parameters 

`driver`  

The Smart Card token driver.

`smartCard`  

The detected Smart Card.

`AID`  

The ISO 7816-4 application identifier that is selected on the Smart Card. If the `com.apple.ctk.aid` attributes is not present in the Smart Card token extension property list, no application is selected.

## Return Value

The token created for the Smart Card, or `nil` if an error occurs or the delegate decides not to provide a token.

