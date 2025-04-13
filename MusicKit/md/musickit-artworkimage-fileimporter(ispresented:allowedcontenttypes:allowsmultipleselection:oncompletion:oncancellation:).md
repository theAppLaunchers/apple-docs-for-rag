

- MusicKit
- ArtworkImage
-  fileImporter(isPresented:allowedContentTypes:allowsMultipleSelection:onCompletion:onCancellation:) 

Instance Method

# fileImporter(isPresented:allowedContentTypes:allowsMultipleSelection:onCompletion:onCancellation:)

Presents a system dialog for allowing the user to import multiple files.

MusicKitSwiftUIiOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+visionOS 1.0+

``` source
nonisolated
func fileImporter(
    isPresented: Binding,
    allowedContentTypes: [UTType],
    allowsMultipleSelection: Bool,
    onCompletion: @escaping (Result) -> Void,
    onCancellation: @escaping () -> Void
) -> some View
```

## Parameters 

`isPresented`  

A binding to whether the dialog should be shown.

`allowedContentTypes`  

The list of supported content types which can be imported.

`allowsMultipleSelection`  

Whether the importer allows the user to select more than one file to import.

`onCompletion`  

A callback that will be invoked when the operation has succeeded or failed. The `result` indicates whether the operation succeeded or failed. To access the received URLs, call `startAccessingSecurityScopedResource`. When the access is no longer required, call `stopAccessingSecurityScopedResource`.

`onCancellation`  

A callback that will be invoked if the user cancels the operation.

## Discussion

In order for the dialog to appear, `isPresented` must be `true`. When the operation is finished, `isPresented` will be set to `false` before `onCompletion` is called. If the user cancels the operation, `isPresented` will be set to `false` and `onCompletion` will not be called.

Note

This dialog provides security-scoped URLs. Call the `startAccessingSecurityScopedResource` method to access or bookmark the URLs, and the `stopAccessingSecurityScopedResource` method to release the access.

For example, a button that allows the user to choose multiple PDF files for the application to combine them later, might look like this:

```
   struct PickPDFsButton: View {
       @State private var showFileImporter = false
       var handlePickedPDF: (URL) -> Void

       var body: some View {
           Button {
               showFileImporter = true
           } label: {
               Label("Choose PDFs to combine", systemImage: "doc.circle")
           }
           .fileImporter(
               isPresented: $showFileImporter,
               allowedContentTypes: [.pdf],
               allowsMultipleSelection: true
           ) { result in
               switch result {
               case .success(let files):
                   files.forEach { file in
                       // gain access to the directory
                       let gotAccess = file.startAccessingSecurityScopedResource()
                       if !gotAccess { return }
                       // access the directory URL
                       // (read templates in the directory, make a bookmark, etc.)
                       handlePickedPDF(file)
                       // release access
                       file.stopAccessingSecurityScopedResource()
                   }
               case .failure(let error):
                   // handle error
                   print(error)
               }
           }
       }
   }
```

Note

Changing `allowedContentTypes` or `allowsMultipleSelection` while the file importer is presented will have no immediate effect, however will apply the next time it is presented.

