

- Foundation
- URL
-  export(to:contentType:) 

Instance Method

# export(to:contentType:)

Using the type’s `Transferable` conformance implementation, exports a value by writing it to a provided destination directory.

FoundationCoreTransferableiOS 18.2+iPadOS 18.2+Mac Catalyst 18.2+macOS 15.2+tvOS 18.2+visionOS 2.2+watchOS 11.2+

``` source
func export(
    to destinationDirectory: URL,
    contentType: UTType?
) async throws -> URL
```

## Parameters 

`destinationDirectory`  

A directory to write the file to.

`contentType`  

A content type of the requested file. If `nil`, the first transfer representation is be used.

## Return Value

A URL of the created file. The file is owned by the application, and it is responsible for removing it when the file is not needed anymore.

## Discussion

If the `Transferable` is not backed by a file, this will write the data to specified destination. This function uses the first representation provided for a given type in `static var transferRepresentation` requirement of the `Transferable` protocol or in the `body` of a custom `TransferRepresentation`.

The default implementation of this function is available to all types that conform to `Transferable` protocol.

