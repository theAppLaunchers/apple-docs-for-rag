

- Swift
- String
-  init(importing:contentType:) 

Initializer

# init(importing:contentType:)

Using the type’s `Transferable` conformance implementation, instantiates a value from given data.

SwiftCoreTransferableiOS 18.2+iPadOS 18.2+Mac Catalyst 18.2+macOS 15.2+tvOS 18.2+visionOS 2.2+watchOS 11.2+

``` source
init(
    importing data: Data,
    contentType: UTType?
) async throws
```

## Parameters 

`data`  

Binary data that can be used to instantiate an item

`contentType`  

A content type that corresponds to the structure of the data. If no content type is provided, the framework calls into every transfer representation provided in the implementation of the `Transferable` conformance (`transferRepresentation` static property) until it finds one that can handle the data.

## Discussion

The default implementation of this initializer is available to all types that conform to `Transferable` protocol.

