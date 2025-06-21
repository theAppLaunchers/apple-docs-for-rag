*   [Local Authentication](/documentation/localauthentication)
*   LAPersistedRight

Class

# LAPersistedRight

A right that gates access to a key and a secret.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class LAPersistedRight
```
```
```
```
```
```
```
```

## [Overview](/documentation/LocalAuthentication/LAPersistedRight#overview)

An [`LAPersistedRight`](/documentation/localauthentication/lapersistedright) is a right that’s backed by a unique key in the Secure Enclave with an access control list that matches the authorization requirements of the right. You can access the key that backs a right to perform cryptographic operations like encryption, decryption, signing, and verification.

You can use the key that backs an [`LAPersistedRight`](/documentation/localauthentication/lapersistedright) to perform both public key and private key operations, but private key operations — like decryption, signing, and key exchange — are only available after you authorize the right. Public key operations like encryption and verification are always available.

The following generates a right with the default authorization requirements, stores it in the [`shared`](/documentation/localauthentication/larightstore/shared) [`LARightStore`](/documentation/localauthentication/larightstore), and exports the public key so that you can use it to verify signatures that the corresponding private key produces:

```swift
```swift
```swift
```swift
```swift
```swift
func generateClientKeys() async throws -> Data {
```
```
    let right = LARight()
    let persistedRight = try await LARightStore.shared.saveRight(right, identifier: "server-access")
    return try await persistedRight.key.publicKey.bytes
}
```
```
```
```

The following uses the private key associated with the right from the previous example to sign a challenge issued by a server:

```swift
```swift
```swift
```swift
```swift
```swift
func signServerChallenge(nonce: Data) async throws -> Data {
```
```
    let persistedRight = try await LARightStore.shared.right(forIdentifier: "server-access")
    try await persistedRight.authorize(localizedReason: "Access the sandcastle competition server")
    guard persistedRight.key.canSign(using: .ecdsaSignatureMessageX962SHA256) else {
        throw NSError(domain: "ExampleErrorDomain", code: -1, userInfo: [:])
    }
    
    return try await persistedRight.key.sign(nonce, algorithm: .ecdsaSignatureMessageX962SHA256)
}
```
```
```
```

The signature operation occurs after verifying that the user has the proper authorization and confirming that the private key supports the given signing algorithm.

## [Topics](/documentation/LocalAuthentication/LAPersistedRight#topics)

### [Accessing persistent data](/documentation/LocalAuthentication/LAPersistedRight#Accessing-persistent-data)

```swift
```swift
```swift
```swift
var key: LAPrivateKey
```
```

The private key that’s persisted by the right.
```
```swift
```swift
```swift
var secret: LASecret
```
```

The data kept secret by the right.
```
```

## [Relationships](/documentation/LocalAuthentication/LAPersistedRight#relationships)

### [Inherits From](/documentation/LocalAuthentication/LAPersistedRight#inherits-from)

*   [`LARight`](/documentation/localauthentication/laright)

### [Conforms To](/documentation/LocalAuthentication/LAPersistedRight#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)

## [See Also](/documentation/LocalAuthentication/LAPersistedRight#see-also)

### [Persistence](/documentation/LocalAuthentication/LAPersistedRight#Persistence)

```swift
```swift
```swift
```swift
class LARightStore
```
```

A container for data protected by a right.
```
```swift
```swift
```swift
class LASecret
```
```

Data that’s protected by a persisted right.
```
```