

- AppKit
- NSWindow
-  drag(\_:at:offset:event:pasteboard:source:slideBack:) Deprecated

Instance Method

# drag(\_:at:offset:event:pasteboard:source:slideBack:)

Begins a dragging session.

macOS 10.0–15.4Deprecated

``` source
@MainActor
func drag(
    _ image: NSImage,
    at baseLocation: NSPoint,
    offset initialOffset: NSSize,
    event: NSEvent,
    pasteboard pboard: NSPasteboard,
    source sourceObj: Any,
    slideBack slideFlag: Bool
)
```

Deprecated

Use -\[NSWindow beginDraggingSessionWithItems:event:source:\] instead.

## Parameters 

`image`  

The object to be dragged.

`baseLocation`  

Location of the image’s bottom-left corner in the window’s coordinate system. It determines the placement of the dragged image under the pointer.

`initialOffset`  

The pointer’s location relative to the mouse-down location. Not used in macOS 10.4 and later.

`event`  

The left-mouse down event that triggered the dragging operation.

`pboard`  

The pasteboard that holds the data to be transferred to the destination.

`sourceObj`  

The object serving as the controller of the dragging operation. It must conform to the NSDraggingSource protocol.

`slideFlag`  

Specifies whether the drag image should slide back to `baseLocation` if it’s rejected by the drag destination. Pass true to specify slide back behavior or false to specify that it should not.

## Discussion

This method should be invoked only from within a view’s implementation of the mouseDown(with:) or mouseDragged(with:) methods (which overrides the version defined in `NSResponder` class). Essentially the same as the `NSView` method of the same name, except that `baseLocation` is given in the `NSWindow` object’s base coordinate system.

## See Also

### Dragging Items

func registerForDraggedTypes([NSPasteboard.PasteboardType])

Registers a set of pasteboard types that the window accepts as the destination of an image-dragging session.

func unregisterDraggedTypes()

Unregisters the window as a possible destination for dragging operations.

