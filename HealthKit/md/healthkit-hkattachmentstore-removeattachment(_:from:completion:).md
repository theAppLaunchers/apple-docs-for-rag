

- HealthKit
- HKAttachmentStore
-  removeAttachment(\_:from:completion:) 

Instance Method

# removeAttachment(\_:from:completion:)

Removes the specified attachment.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+visionOS 1.0+watchOS 9.0+

``` source
func removeAttachment(
    _ attachment: HKAttachment,
    from object: HKObject,
    completion: @escaping (Bool, (any Error)?) -> Void
)
```

``` source
func removeAttachment(
    _ attachment: HKAttachment,
    from object: HKObject
) async throws
```

## Parameters 

`attachment`  

An attachment associated with the specified object.

`object`  

An object from the HealthKit store.

`completion`  

A completion handler that the system calls after removing the attachment. This handler takes the following parameters:

success  
A Boolean value that indicates whether the system successfully removed the attachment.

error  
If an error occurred, this parameter contains information about the error. Otherwise, it’s `nil`.

## Discussion

Use this method to remove an attachment from an object saved in the HealthKit store.

```
// Remove the attachment from the specified object.
do {
    try await attachmentStore.removeAttachment(myAttachment, from: myObject)
} catch {
    // Handle the error here.
    fatalError("*** An error occurred while removing an attachment: \(error.localizedDescription) ***")
}
```

