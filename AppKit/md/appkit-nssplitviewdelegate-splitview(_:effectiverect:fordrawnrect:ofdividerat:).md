

- AppKit
- NSSplitViewDelegate
-  splitView(\_:effectiveRect:forDrawnRect:ofDividerAt:) 

Instance Method

# splitView(\_:effectiveRect:forDrawnRect:ofDividerAt:)

Allows the delegate to modify the rectangle where mouse clicks initiate divider dragging.

macOS 10.5+

``` source
@MainActor
optional func splitView(
    _ splitView: NSSplitView,
    effectiveRect proposedEffectiveRect: NSRect,
    forDrawnRect drawnRect: NSRect,
    ofDividerAt dividerIndex: Int
) -> NSRect
```

## Parameters 

`splitView`  

The split view that sends the message.

`proposedEffectiveRect`  

The proposed rectangle where mouse clicks initiate divider dragging. The rectangle uses the coordinate system that `splitView` defines.

`drawnRect`  

The frame of the divider in the coordinate system that `splitView` defines.

`dividerIndex`  

The index of the divider.

## Return Value

A rectangle, in the coordinate system that `splitView` defines, where mouse clicks initiate divider dragging.

## Discussion

A split view with thick dividers proposes the drawn frame as the effective frame. A split view with thin dividers proposes an effective frame that’s a little larger than the drawn frame to make it easier for the user to grab the divider.

If a split view has no delegate, or if its delegate doesn’t respond to this message, the split view behaves as if it has a delegate that returns `proposedEffectiveRect` when it receives this message.

## See Also

### Configuring and Drawing View Dividers

func splitView(NSSplitView, shouldHideDividerAt: Int) -> Bool

Allows the delegate to determine whether the user can drag a divider or adjust it off the edge of the split view.

func splitView(NSSplitView, additionalEffectiveRectOfDividerAt: Int) -> NSRect

Allows the delegate to return an additional rectangle where mouse clicks can initiate divider dragging.

