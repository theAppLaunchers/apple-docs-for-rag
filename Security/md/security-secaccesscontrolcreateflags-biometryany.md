

- Security
- SecAccessControlCreateFlags
-  biometryAny 

Type Property

# biometryAny

Constraint to access an item with Touch ID for any enrolled fingers, or Face ID.

iOS 11.3+iPadOS 11.3+Mac Catalyst 13.1+macOS 10.13.4+tvOS 11.3+visionOS 1.0+watchOS 4.3+

``` source
static var biometryAny: SecAccessControlCreateFlags { get }
```

## Mentioned in 

Protecting keys with the Secure Enclave

## Discussion

Touch ID must be available and enrolled with at least one finger, or Face ID must be available and enrolled. The item is still accessible by Touch ID if fingers are added or removed, or by Face ID if the user is re-enrolled.

