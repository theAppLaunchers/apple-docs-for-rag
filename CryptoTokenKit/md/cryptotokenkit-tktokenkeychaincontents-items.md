

- CryptoTokenKit
- TKTokenKeychainContents
-  items 

Instance Property

# items

Returns all items for token in the keychain.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.12+tvOS 11.0+visionOS 1.0+watchOS 4.0+

``` source
var items: [TKTokenKeychainItem] { get }
```

## See Also

### Accessing Keychain Items

func key(forObjectID: TKToken.ObjectID) throws -> TKTokenKeychainKey

Returns the key for a specified object identifier.

func certificate(forObjectID: TKToken.ObjectID) throws -> TKTokenKeychainCertificate

Returns the key for a specified object identifier.

