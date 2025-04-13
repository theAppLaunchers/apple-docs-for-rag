

- AppKit
- NSSplitViewDelegate
-  splitView(\_:constrainMaxCoordinate:ofSubviewAt:) 

Instance Method

# splitView(\_:constrainMaxCoordinate:ofSubviewAt:)

Allows the delegate to constrain the maximum coordinate limit of a divider when the user drags it.

macOS 10.0+

``` source
@MainActor
optional func splitView(
    _ splitView: NSSplitView,
    constrainMaxCoordinate proposedMaximumPosition: CGFloat,
    ofSubviewAt dividerIndex: Int
) -> CGFloat
```

## Parameters 

`splitView`  

The split view that sends the message.

`proposedMaximumPosition`  

The proposed maximum coordinate limit of the subview in the split view’s flipped coordinate system.

`dividerIndex`  

Specifies the divider the user is moving, with the first divider being 0 and increasing from top to bottom (or left to right).

## Return Value

The maximum coordinate limit of the divider.

## Discussion

Important

If your split view uses Auto Layout to size its subviews, don’t implement this method.

The delegate receives this message before the split view begins tracking the mouse to position a divider. You can further constrain the limits, but you can’t extend the divider limits.

If the split bars are horizontal (views are one on top of the other), `proposedMax` is the bottom limit. If the split bars are vertical (views are side by side), `proposedMax` is the right limit. The initial value of `proposedMax` is the bottom (or right side) of the subview after the divider.

## See Also

### Adjusting Subviews Manually

func splitView(NSSplitView, constrainMinCoordinate: CGFloat, ofSubviewAt: Int) -> CGFloat

Allows the delegate to constrain the minimum coordinate limit of a divider when the user drags it.

func splitView(NSSplitView, resizeSubviewsWithOldSize: NSSize)

Allows the delegate to specify custom sizing behavior for the subviews of the split view.

func splitView(NSSplitView, shouldAdjustSizeOfSubview: NSView) -> Bool

Allows the delegate to specify whether to resize the subview.

