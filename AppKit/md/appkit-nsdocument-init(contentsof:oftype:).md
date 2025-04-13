

- AppKit
- NSDocument
-  init(contentsOf:ofType:) 

Initializer

# init(contentsOf:ofType:)

Initializes a document located by a URL of a specified type.

macOS

``` source
@MainActor
convenience init(
    contentsOf url: URL,
    ofType typeName: String
) throws
```

## Parameters 

`url`  

The URL from which the contents of the document are obtained.

`typeName`  

The string that identifies the document type.

## Return Value

The initialized `NSDocument` object, or, if the document could not be created, `nil`.

## Discussion

You can override this method to customize the reopening of autosaved documents.

This method is invoked by the `NSDocumentController` method makeDocument(withContentsOf:ofType:). The default implementation of this method calls the init() and read(from:ofType:) methods and sets values for the fileURL, fileType, and fileModificationDate properties.

For backward binary compatibility with OS X v10.3 and earlier, the default implementation of this method instead invokes initWithContentsOfFile:ofType: if it is overridden and the URL uses the `file:` scheme. It still updates the fileModificationDate property in this situation.

Handling Errors in Swift

In Swift, this method is marked with the `throws` keyword to indicate that it throws an error in cases of failure.

When overriding this method, use the `throw` statement to throw an `NSError`, as described in Error Handling in The Swift Programming Language and `About Imported Cocoa Error Parameters`.

## See Also

### Creating a Document Object

init()

Initializes and returns an empty document object.

convenience init(for: URL?, withContentsOf: URL, ofType: String) throws

Initializes a document with the specified contents, and places the resulting document’s file at the designated location.

convenience init(type: String) throws

Initializes a document of a specified type.

