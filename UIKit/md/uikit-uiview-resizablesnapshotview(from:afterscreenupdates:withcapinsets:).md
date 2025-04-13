

- UIKit
- UIView
-  resizableSnapshotView(from:afterScreenUpdates:withCapInsets:) 

Instance Method

# resizableSnapshotView(from:afterScreenUpdates:withCapInsets:)

Returns a snapshot view based on the specified contents of the current view, with stretchable insets.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
func resizableSnapshotView(
    from rect: CGRect,
    afterScreenUpdates afterUpdates: Bool,
    withCapInsets capInsets: UIEdgeInsets
) -> UIView?
```

## Parameters 

`rect`  

The portion of the view that you want to capture. The rectangle must be in the bounds coordinate space of the current view.

`afterUpdates`  

A Boolean value that specifies whether the snapshot should be taken after recent changes have been incorporated. Pass the value false if you want to capture the screen in its current state, which might not include recent changes.

`capInsets`  

The edge insets that define the stretchable portion of the returned view’s content. You can specify zero if you do not want the contents of the returned view to have a stretchable area.

## Return Value

A new view object containing a snapshot of the current view’s rendered contents.

## Discussion

This method very efficiently captures the current rendered appearance of a view and uses it to build a new snapshot view with stretchable insets. You can use the returned view as a visual stand-in for the current view in your app. For example, you might use a snapshot view for animations where updating a large view hierarchy might be expensive. Because the content is captured from the already rendered content, this method reflects the current visual appearance of the view and is not updated to reflect animations that are scheduled or in progress. However, calling this method is faster than trying to render the contents of the current view into a bitmap image yourself.

Because the returned snapshot is a view object, you can modify it and its layer object as needed. However, you cannot change the contents property of the snapshot view’s layer; attempts to do so fail silently. If the current view is not yet rendered, perhaps because it is not yet onscreen, the snapshot view has no visible content.

You can call this method on a previously generated snapshot to obtain a new snapshot. For example, you could do so after you change properties of a previous snapshot (such as its alpha value) and want a new snapshot that includes those changes.

If you want to apply a graphical effect, such as blur, to a snapshot, use the drawHierarchy(in:afterScreenUpdates:) method instead.

If you specify nonzero edge insets in the `capInsets` parameter, those values determine the returned snapshot’s stretchable content area.

## See Also

### Capturing a view snapshot

func snapshotView(afterScreenUpdates: Bool) -> UIView?

Returns a snapshot view based on the contents of the current view.

func drawHierarchy(in: CGRect, afterScreenUpdates: Bool) -> Bool

Renders a snapshot of the complete view hierarchy as visible onscreen into the current context.

