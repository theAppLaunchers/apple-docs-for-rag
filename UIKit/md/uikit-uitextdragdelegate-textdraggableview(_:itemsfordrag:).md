

- UIKit
- UITextDragDelegate
-  textDraggableView(\_:itemsForDrag:) 

Instance Method

# textDraggableView(\_:itemsForDrag:)

Asks the delegate for custom drag items from a text view.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
@MainActor
optional func textDraggableView(
    _ textDraggableView: any UIView & UITextDraggable,
    itemsForDrag dragRequest: any UITextDragRequest
) -> [UIDragItem]
```

## Parameters 

`textDraggableView`  

The text view where the drag activity was started.

`dragRequest`  

The current drag request.

## Return Value

An array of drag items that represent the items to drag.

## Discussion

You implement this method when you need to provide custom drag items. The drag request gives you the text range of the text that is included in the drag activity. It also gives you the default drag items, which you can add to or change. If you return an empty array, the drag operation does not happen.

Note

This method may be called more than once. For instance, it is called each time the user adds more drag items to the session. You can detect additional calls to this method by checking the existingItems property on the drag request.

