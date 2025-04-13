

- Swift
- Never
-  init(importing:contentType:) 

Initializer

# init(importing:contentType:)

Using the type’s `Transferable` conformance implementation, instantiates a value from the given file.

SwiftCoreTransferableiOS 18.2+iPadOS 18.2+Mac Catalyst 18.2+macOS 15.2+tvOS 18.2+visionOS 2.2+watchOS 11.2+

``` source
init(
    importing file: URL,
    contentType: UTType?
) async throws
```

## Parameters 

`file`  

A URL to a file on disk.

`contentType`  

An optional content type for creating a value. If a value is not provided, the initializer tries to infer it from the file extension or its metadata. If the content type is still unknown, the framework calls the first transfer representation with this URL. If the item isn’t imported successfully, the framework calls the second representation and so on.

## Discussion

The default implementation of this initializer is available to all types that conform to `Transferable` protocol.

