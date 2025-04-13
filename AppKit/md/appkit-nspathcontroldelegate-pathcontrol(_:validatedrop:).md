

- AppKit
- NSPathControlDelegate
-  pathControl(\_:validateDrop:) 

Instance Method

# pathControl(\_:validateDrop:)

Implement this method to enable dragging onto the control.

macOS 10.5+

``` source
@MainActor
optional func pathControl(
    _ pathControl: NSPathControl,
    validateDrop info: any NSDraggingInfo
) -> NSDragOperation
```

## Parameters 

`pathControl`  

The path control that sent the message.

`info`  

An object containing details about this dragging operation.

## Discussion

This method is called when something is dragged over the control. Return `NSDragOperationNone` to refuse the drop, or return anything else to accept it.

If not implemented, and the control’s cell is editable, the drop is accepted if it contains an `NSURLPboardType` or `NSFilenamesPboardType` that conforms to the cell’s allowed types. Implementation of this method is optional.

## See Also

### Dragging Support

func pathControl(NSPathControl, shouldDrag: NSPathComponentCell, with: NSPasteboard) -> Bool

Implement this method to enable dragging from the control.

func pathControl(NSPathControl, acceptDrop: any NSDraggingInfo) -> Bool

Implement this method to accept previously validated contents dropped onto the control.

