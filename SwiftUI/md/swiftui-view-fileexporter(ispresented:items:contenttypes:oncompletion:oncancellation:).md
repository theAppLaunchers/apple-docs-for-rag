

- SwiftUI
- View
-  fileExporter(isPresented:items:contentTypes:onCompletion:onCancellation:) 

Instance Method

# fileExporter(isPresented:items:contentTypes:onCompletion:onCancellation:)

Presents a system interface allowing the user to export a collection of items to files on disk.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+visionOS 1.0+

``` source
nonisolated
func fileExporter(
    isPresented: Binding,
    items: C,
    contentTypes: [UTType] = [],
    onCompletion: @escaping (Result) -> Void,
    onCancellation: @escaping () -> Void = { }
) -> some View where C : Collection, T : Transferable, T == C.Element
```

## Parameters 

`isPresented`  

A binding to whether the interface should be shown.

`items`  

Collection of values to be saved on disk.

`contentTypes`  

The content types to use for the exported file. If empty, SwiftUI uses the content types from the `transferRepresentation` property provided for `Transferable` conformance.

`onCompletion`  

A callback that will be invoked when the operation has has succeeded or failed.

`onCancellation`  

A callback that will be invoked if the operation was cancelled.

## Discussion

In order for the interface to appear `isPresented` must be set to `true`. When the operation is finished, `isPresented` will be set to `false` before `onCompletion` is called. If the user cancels the operation, `isPresented` will be set to `false` and `onCompletion` will not be called.

## See Also

### Exporting to file

func fileExporter(isPresented:document:contentType:defaultFilename:onCompletion:)

Presents a system interface for exporting a document that’s stored in a value type, like a structure, to a file on disk.

func fileExporter(isPresented:documents:contentType:onCompletion:)

Presents a system interface for exporting a collection of value type documents to files on disk.

func fileExporter(isPresented:document:contentTypes:defaultFilename:onCompletion:onCancellation:)

Presents a system interface for allowing the user to export a `FileDocument` to a file on disk.

func fileExporter(isPresented:documents:contentTypes:onCompletion:onCancellation:)

Presents a system dialog for allowing the user to export a collection of documents that conform to `FileDocument` to files on disk.

func fileExporter&lt;T>(isPresented: Binding&lt;Bool>, item: T?, contentTypes: [UTType], defaultFilename: String?, onCompletion: (Result&lt;URL, any Error>) -> Void, onCancellation: () -> Void) -> some View

Presents a system interface allowing the user to export a `Transferable` item to file on disk.

func fileExporterFilenameLabel(_:)

On macOS, configures the `fileExporter` with a text to use as a label for the file name field.

