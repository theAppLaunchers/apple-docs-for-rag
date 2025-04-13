

- AppKit
- NSDocument
-  autosave(withImplicitCancellability:completionHandler:) 

Instance Method

# autosave(withImplicitCancellability:completionHandler:)

Autosaves the document’s contents to an appropriate file-system location, as needed.

macOS 10.7+

``` source
@MainActor
func autosave(
    withImplicitCancellability autosavingIsImplicitlyCancellable: Bool,
    completionHandler: @escaping ((any Error)?) -> Void
)
```

``` source
@MainActor
func autosave(withImplicitCancellability autosavingIsImplicitlyCancellable: Bool) async throws
```

## Parameters 

`autosavingIsImplicitlyCancellable`  

The value in the autosavingIsImplicitlyCancellable property while autosaving is happening.

`completionHandler`  

The completion handler block object passed in to be invoked at some point in the future, perhaps after the method invocation has returned. The completion handler must be invoked on the main thread.

The block takes one argument:

`errorOrNil`  
If successful, pass a `nil` error. If not successful, pass an `NSError` object that encapsulates the reason why the document could not be autosaved.

## Discussion

The default implementation of this method does the following:

1.  Checks the value of the hasUnautosavedChanges property.

2.  If the value of that property is false, the method runs the completion handler with a `nil` error and returns immediately.

If the value is true, calls autosavesInPlace on the class to determine where the autosaved document contents should go.

The method also gets the value in fileURL to ensure that the file has an actual URL, because it is not possible to autosave in place if the document does not yet have a permanent location. 3. Checks the value in the autosavingFileType property to determine the file type for the autosaved file. 4. Calls save(to:ofType:for:completionHandler:).

The value of the `saveToURL` parameter is the location where the file should be saved. If the file has a URL and the class specifies that autosave should occur in place, this is the URL of the file. Otherwise, this is the location of a nonexistent file in the specified autosave location.

The value for the `ofType` parameter is determined by a call to autosavingFileType.

The value of the `forSaveOperation` parameter is `NSAutosaveInPlaceOperation` if the class is configured to autosave in place and the file has a URL. Otherwise, the value is `NSAutosaveElsewhereOperation`.

## See Also

### Autosaving the Document

func checkAutosavingSafety() throws

Returns a Boolean value that indicates whether it is safe to autosave document changes.

var hasUnautosavedChanges: Bool

A Boolean value that indicates whether the document has changes that have not been autosaved.

func scheduleAutosaving()

Schedules periodic autosaving for the purpose of crash protection.

func autosave(withDelegate: Any?, didAutosave: Selector?, contextInfo: UnsafeMutableRawPointer?)

Autosaves the document’s contents to an appropriate location in the file system.

var backupFileURL: URL?

The URL for the document’s backup file that was created during an autosave operation.

