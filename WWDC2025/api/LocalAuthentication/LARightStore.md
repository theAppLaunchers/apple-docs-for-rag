*   [Local Authentication](/documentation/localauthentication)
*   LARightStore

Class

# LARightStore

A container for data protected by a right.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class LARightStore
```
```
```
```
```
```
```
```

## [Overview](/documentation/LocalAuthentication/LARightStore#overview)

Use an [`LARightStore`](/documentation/localauthentication/larightstore) along with an [`LARight`](/documentation/localauthentication/laright) to make secrets accessible only after certain conditions, including authentication, are met. Storing secrets this way lets you tie the availability of sensitive resources to the authorization status of the user.

The following stores a named access token behind the default authorization requirements:

```swift
```swift
```swift
```swift
```swift
```swift
func storeBackendAccessToken(_ token: Data) async throws {
```
```
    let loginRight = LARight()
    _ = try await LARightStore.shared.saveRight(loginRight, identifier: "access-token", secret: token)
}
```
```
```
```

The system stores your secret in the keychain and protects it with a unique key in the Secure Enclave. The system associates the key with your right and with an access control list that ensures that the data is only accessible after your access requirements are met.

You can retrieve stored secrets later using the right’s identifier:

```swift
```swift
```swift
```swift
```swift
```swift
func fetchBackendAccessToken() async throws -> Data {
```
```
    let loginRight = try await LARightStore.shared.right(forIdentifier: "access-token")
    // Authorize the right or else the secret is unavailable.
    try await loginRight.authorize(localizedReason: "Access sandcastle competition server")
    return try await loginRight.secret.rawData
}
```
```
```
```

## [Topics](/documentation/LocalAuthentication/LARightStore#topics)

### [Accessing rights](/documentation/LocalAuthentication/LARightStore#Accessing-rights)

```swift
```swift
```swift
```swift
class var shared: LARightStore
```
```

A shared object that stores rights.
```
```swift
```swift
```swift
func right(forIdentifier: String, completion: (LAPersistedRight?, (any Error)?) -> Void)
```
```

Fetches a previously stored right from the shared right store.
```
```

### [Storing rights](/documentation/LocalAuthentication/LARightStore#Storing-rights)

```swift
```swift
```swift
```swift
func saveRight(LARight, identifier: String, completion: (LAPersistedRight?, (any Error)?) -> Void)
```
```

Saves a right to a persistent right store.
```
```swift
```swift
```swift
func saveRight(LARight, identifier: String, secret: Data, completion: (LAPersistedRight?, (any Error)?) -> Void)
```
```

Saves a right to a persistent store along with secret data you supply.
```
```

### [Removing stored rights](/documentation/LocalAuthentication/LARightStore#Removing-stored-rights)

```swift
```swift
```swift
```swift
func removeRight(LAPersistedRight, completion: ((any Error)?) -> Void)
```
```

Removes a right from the right store given an instance of that right.
```
```swift
```swift
```swift
func removeRight(forIdentifier: String, completion: ((any Error)?) -> Void)
```
```

Removes a right from the right store given its unique identifier.
```
```swift
```swift
```swift
func removeAllRights(completion: ((any Error)?) -> Void)
```
```

Removes all rights associated with this client from the right store.
```
```

## [Relationships](/documentation/LocalAuthentication/LARightStore#relationships)

### [Inherits From](/documentation/LocalAuthentication/LARightStore#inherits-from)

*   [`NSObject`](/documentation/ObjectiveC/NSObject-swift.class)

### [Conforms To](/documentation/LocalAuthentication/LARightStore#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)

## [See Also](/documentation/LocalAuthentication/LARightStore#see-also)

### [Persistence](/documentation/LocalAuthentication/LARightStore#Persistence)

```swift
```swift
```swift
```swift
class LAPersistedRight
```
```

A right that gates access to a key and a secret.
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