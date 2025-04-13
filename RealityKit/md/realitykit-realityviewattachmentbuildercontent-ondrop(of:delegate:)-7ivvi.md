

- RealityKit
- RealityViewAttachmentBuilderContent
-  onDrop(of:delegate:) 

Instance Method

# onDrop(of:delegate:)

Defines the destination of a drag and drop operation using behavior controlled by the delegate that you provide.

RealityKitSwiftUIiOS 14.0+iPadOS 14.0+macOS 11.0+visionOS

``` source
nonisolated
func onDrop(
    of supportedContentTypes: [UTType],
    delegate: any DropDelegate
) -> some View
```

## Parameters 

`supportedContentTypes`  

The uniform type identifiers that describe the types of content this view can accept through drag and drop. If the drag and drop operation doesn’t contain any of the supported types, then this drop destination doesn’t activate and `isTargeted` doesn’t update.

`delegate`  

A type that conforms to the `DropDelegate` protocol. You have comprehensive control over drop behavior when you use a delegate.

## Return Value

A view that provides a drop destination for a drag operation of the specified types.

## Discussion

The drop destination is the same size and position as this view.

