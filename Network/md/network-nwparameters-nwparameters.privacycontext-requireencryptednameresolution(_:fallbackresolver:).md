

- Network
- NWParameters
- NWParameters.PrivacyContext
-  requireEncryptedNameResolution(\_:fallbackResolver:) 

Instance Method

# requireEncryptedNameResolution(\_:fallbackResolver:)

Requires that any DNS name resolution for connections associated with this context use encrypted transports, such as TLS or HTTPS.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+watchOS 7.0+

``` source
func requireEncryptedNameResolution(
    _ requireEncryption: Bool,
    fallbackResolver: NWParameters.PrivacyContext.ResolverConfiguration?
)
```

## Parameters 

`requireEncryption`  

A Boolean that indicates whether your connections prohibits unencrypted name resolution.

`fallbackResolver`  

An encrypted DNS resolver configuration that your connections use if the system doesn’t have a preferred encrypted resolver.

## Discussion

Connections that use iCloud Private Relay automatically use encrypted name resolution. When active, name resolution uses iCloud Private Relay instead of the `fallbackResolver`.

## See Also

### Requiring Encrypted DNS

enum ResolverConfiguration

A DNS server configuration that uses TLS or HTTPS.

