

- Core Transferable
- FileRepresentation
-  init(importedContentType:shouldAttemptToOpenInPlace:importing:) 

Initializer

# init(importedContentType:shouldAttemptToOpenInPlace:importing:)

Creates a transfer representation for importing transferable items as files.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
init(
    importedContentType: UTType,
    shouldAttemptToOpenInPlace: Bool = false,
    importing: @escaping (ReceivedTransferredFile) async throws -> Item
)
```

## Parameters 

`importedContentType`  

A uniform type identifier for the file promise, returned by the `exporting` closure.

`shouldAttemptToOpenInPlace`  

A Boolean value that indicates whether the receiver wants to gain access to the original item on disk and can edit it. If `false`, the receiver only has access to a copy of the file made by the system.

`importing`  

A closure that creates the item with given file promise. The file referred to by the `file` property of the `ReceivedTransferredFile` is only guaranteed to exist within the `importing` closure. If you need the file to be around for a longer period, make a copy in the `importing` closure.

## See Also

### Creating a transfer representation

init(contentType: UTType, shouldAttemptToOpenInPlace: Bool, exporting: (Item) async throws -> SentTransferredFile, importing: (ReceivedTransferredFile) async throws -> Item)

Creates a transfer representation for importing and exporting transferable items as files.

init(exportedContentType: UTType, shouldAllowToOpenInPlace: Bool, exporting: (Item) async throws -> SentTransferredFile)

Creates a transfer representation for exporting transferable items as files.

