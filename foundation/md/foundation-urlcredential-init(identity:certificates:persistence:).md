

- Foundation
- URLCredential
-  init(identity:certificates:persistence:) 

Initializer

# init(identity:certificates:persistence:)

Creates a URL credential instance for resolving a client certificate authentication challenge.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.1+macOS 10.6+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
init(
    identity: SecIdentity,
    certificates certArray: [Any]?,
    persistence: URLCredential.Persistence
)
```

## Parameters 

`identity`  

The identity for the credential.

`certArray`  

An array of one or more `SecCertificateRef` objects representing intermediate certificates leading from the identity’s certificate to a trusted root, or `nil` if the server does not need any intermediate certificates to authenticate the client.

`persistence`  

The method ignores this parameter; you should supply a value of URLCredential.Persistence.forSession because that most accurately reflects the actual behaviour.

## Return Value

A new URL credential object, using the provided identity and, optionally, an array of intermediate certificates.

## Discussion

When you receive a client certificate authentication challenge (NSURLAuthenticationMethodClientCertificate) and want to resolve it successfully, you must supply a credential created using this initializer.

In most cases you should pass `nil` to the `certArray` parameter. You only need to supply an array of intermediate certificates if the server needs those intermediate certificates to authenticate the client. Typically this isn’t necessary because the server already has a copy of the relevant intermediate certificates.

## See Also

### Creating a credential

init(forTrust: SecTrust)

Creates a URL credential instance for server trust authentication with a given accepted trust.

init(trust: SecTrust)

Creates a URL credential instance for server trust authentication, initialized with a accepted trust.

init(user: String, password: String, persistence: URLCredential.Persistence)

Creates a URL credential instance initialized with a given user name and password, using a given persistence setting.

enum Persistence

Constants that specify how long the credential will be kept.

