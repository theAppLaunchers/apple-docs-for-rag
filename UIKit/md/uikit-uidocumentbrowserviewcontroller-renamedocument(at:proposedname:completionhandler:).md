

- UIKit
- UIDocumentBrowserViewController
-  renameDocument(at:proposedName:completionHandler:) 

Instance Method

# renameDocument(at:proposedName:completionHandler:)

Renames a document at the specified URL.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+visionOS 1.0+

``` source
@MainActor
func renameDocument(
    at documentURL: URL,
    proposedName: String,
    completionHandler: @escaping (URL?, (any Error)?) -> Void
)
```

``` source
@MainActor
func renameDocument(
    at documentURL: URL,
    proposedName: String
) async throws -> URL
```

## Parameters 

`documentURL`  

The URL specifying the location of the document.

`proposedName`  

The proposed new name to rename the document to. If `proposedName` is already taken, the system might alter the proposed name and confirm the new suggestion with the user. The final name that the system chooses appears in the `finalURL` parameter of `completionHandler`.

`completionHandler`  

A completion handler to execute after the renaming operation occurs. The final URL and error information are available in the completion handler.

`finalURL`  
The URL of the newly renamed document, or `nil` if an error occurs.

`error`  
An object that describes the error, if one occurs; otherwise, `nil`.

