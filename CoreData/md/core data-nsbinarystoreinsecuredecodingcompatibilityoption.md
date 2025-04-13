

- Core Data
-  NSBinaryStoreInsecureDecodingCompatibilityOption 

Global Variable

# NSBinaryStoreInsecureDecodingCompatibilityOption

A flag that indicates Core Data decodes the binary store insecurely.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.13+tvOS 11.0+visionOS 1.0+watchOS 4.0+

``` source
let NSBinaryStoreInsecureDecodingCompatibilityOption: String
```

## Discussion

Use the NSBinaryStoreSecureDecodingClasses option instead, if possible, to allow Core Data to securely decode the binary store.

If a store has metadata or transformable properties that contain nonstandard classes, this option may be appropriate. Apps linked before the availability date default to using this option.

## See Also

### Persistent Store Metadata Keys

let NSBinaryStoreSecureDecodingClasses: String

An additional set of classes to use while decoding a binary store.

let NSPersistentStoreRemoteChangeNotificationPostOptionKey: String

A key that indicates a persistent store posts a remote change notification for every write to the store, including writes by other processes.

let NSPersistentStoreModelVersionChecksumKey: String

