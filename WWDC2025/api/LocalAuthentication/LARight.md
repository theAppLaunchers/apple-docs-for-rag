*   [Local Authentication](/documentation/localauthentication)
*   LARight

Class

# LARight

A grouped set of requirements that gate access to a resource or operation.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class LARight
```
```
```
```
```
```
```
```

## [Overview](/documentation/LocalAuthentication/LARight#overview)

Use [`LARight`](/documentation/localauthentication/laright) instances to protect access to portions of your app that may contain sensitive information. By default, [`LARight`](/documentation/localauthentication/laright) instances require people to authenticate with Face ID, Touch ID, Apple Watch, or the device passcode. The following creates an [`LARight`](/documentation/localauthentication/laright) with the default authentication requirements:

```swift
```swift
```swift
```swift
```swift
```swift
let loginRight = LARight()
```
```
    
```swift
```swift
func login() async throws {
```
```
    try await loginRight.authorize(localizedReason: "Access sandcastle competition designs")
}
```swift
```swift
func logout() async {
```
```
    await loginRight.deauthorize()
}
```
```
```
```

## [Topics](/documentation/LocalAuthentication/LARight#topics)

### [Authorizing a right](/documentation/LocalAuthentication/LARight#Authorizing-a-right)

[`init()`](/documentation/localauthentication/laright/init\(\))

Creates a right using the default authorization requirements.

[`init(requirement: LAAuthenticationRequirement)`](/documentation/localauthentication/laright/init\(requirement:\))

Creates a right with the authentication requirements you supply.

```swift
```swift
```swift
var tag: Int
```
```

An integer you use to identify a right.
```
```swift
```swift
```swift
func authorize(localizedReason: String, completion: ((any Error)?) -> Void)
```
```

Performs an authorization on the right.
```
```swift
```swift
```swift
func authorize(localizedReason: String, in: LAPresentationContext, completion: ((any Error)?) -> Void)
```
```

Performs an authorization on the right with a window context you supply.
```

### [Deauthorizing a right](/documentation/LocalAuthentication/LARight#Deauthorizing-a-right)

```swift
```swift
```swift
```swift
func deauthorize(completion: () -> Void)
```
```

Invalidates a previously authorized right.
```
```

### [Monitoring authorization status](/documentation/LocalAuthentication/LARight#Monitoring-authorization-status)

```swift
```swift
```swift
```swift
func checkCanAuthorize(completion: ((any Error)?) -> Void)
```
```

Checks whether the right has permission to perform authorization.
```
```swift
```swift
```swift
var state: LARight.State
```
```

The current authorization state for a right.
```
```swift
```swift
```swift
enum State
```
```

The possible states for a right during authorization.
```
```

## [Relationships](/documentation/LocalAuthentication/LARight#relationships)

### [Inherits From](/documentation/LocalAuthentication/LARight#inherits-from)

*   [`NSObject`](/documentation/ObjectiveC/NSObject-swift.class)

### [Inherited By](/documentation/LocalAuthentication/LARight#inherited-by)

*   [`LAPersistedRight`](/documentation/localauthentication/lapersistedright)

### [Conforms To](/documentation/LocalAuthentication/LARight#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)

## [See Also](/documentation/LocalAuthentication/LARight#see-also)

### [Authentication and access](/documentation/LocalAuthentication/LARight#Authentication-and-access)

```swift
```swift
```swift
```swift
enum State
```
```

The possible states for a right during authorization.
```
```swift
```swift
```swift
class LAContext
```
```

A mechanism for evaluating authentication policies and access controls.
```
```