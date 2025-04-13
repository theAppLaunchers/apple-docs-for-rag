

- RealityKit
- RealityView
-  fileExporter(isPresented:item:contentTypes:defaultFilename:onCompletion:onCancellation:) 

Instance Method

# fileExporter(isPresented:item:contentTypes:defaultFilename:onCompletion:onCancellation:)

Presents a system interface allowing the user to export a `Transferable` item to file on disk.

RealityKitSwiftUIiOS 17.0+iPadOS 17.0+Mac CatalystmacOS 14.0+visionOS

``` source
nonisolated
func fileExporter(
    isPresented: Binding,
    item: T?,
    contentTypes: [UTType] = [],
    defaultFilename: String? = nil,
    onCompletion: @escaping (Result) -> Void,
    onCancellation: @escaping () -> Void = { }
) -> some View where T : Transferable
```

## Parameters 

`isPresented`  

A binding to whether the interface should be shown.

`item`  

The item to be saved on disk.

`contentTypes`  

The optional content types to use for the exported file. If empty, SwiftUI uses the content types from the `transferRepresentation` property provided for `Transferable` conformance.

`onCompletion`  

A callback that will be invoked when the operation has succeeded or failed.

`onCancellation`  

A callback that will be invoked if the operation was cancelled.

## Discussion

In order for the interface to appear `isPresented` must be set to `true`. When the operation is finished, `isPresented` will be set to `false` before `onCompletion` is called. If the user cancels the operation, `isPresented` will be set to `false` and `onCompletion` will not be called.

