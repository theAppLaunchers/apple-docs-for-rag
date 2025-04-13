

- AppKit
- NSSplitViewController
-  splitView(\_:effectiveRect:forDrawnRect:ofDividerAt:) 

Instance Method

# splitView(\_:effectiveRect:forDrawnRect:ofDividerAt:)

Allows the split view controller to modify the rectangle where mouse clicks initiate divider dragging.

macOS 10.10+

``` source
@MainActor
func splitView(
    _ splitView: NSSplitView,
    effectiveRect proposedEffectiveRect: NSRect,
    forDrawnRect drawnRect: NSRect,
    ofDividerAt dividerIndex: Int
) -> NSRect
```

## See Also

### Configuring and Drawing View Dividers

func splitView(NSSplitView, shouldHideDividerAt: Int) -> Bool

Allows the split view controller to determine whether the user can drag a divider or adjust it off the edge of the split view.

func splitView(NSSplitView, additionalEffectiveRectOfDividerAt: Int) -> NSRect

Allows the split view controller to return an additional rectangle where mouse clicks can initiate divider dragging.

