

- UIKit
- UIView
-  snapshotView(afterScreenUpdates:) 

Instance Method

# snapshotView(afterScreenUpdates:)

Returns a snapshot view based on the contents of the current view.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
func snapshotView(afterScreenUpdates afterUpdates: Bool) -> UIView?
```

## Parameters 

`afterUpdates`  

A Boolean value that specifies whether the snapshot should be taken after recent changes have been incorporated. Pass the value false to capture the screen in its current state, which might not include recent changes.

## Return Value

A new view object based on a snapshot of the current view’s rendered contents.

## Discussion

This method very efficiently captures the current rendered appearance of a view and uses it to build a new snapshot view. You can use the returned view as a visual stand-in for the current view in your app. For example, you might use a snapshot view for animations where updating a large view hierarchy might be expensive. Because the content is captured from the already rendered content, this method reflects the current visual appearance of the view and is not updated to reflect animations that are scheduled or in progress. However, calling this method is faster than trying to render the contents of the current view into a bitmap image yourself.

Because the returned snapshot is a view object, you can modify it and its layer object as needed. However, you cannot change the contents property of the snapshot view’s layer; attempts to do so fail silently. If the current view is not yet rendered, perhaps because it is not yet onscreen, the snapshot view has no visible content.

You can call this method on a previously generated snapshot to obtain a new snapshot. For example, you could do so after you change properties of a previous snapshot (such as its alpha value) and want a new snapshot that includes those changes.

If you want to apply a graphical effect, such as blur, to a snapshot, use the drawHierarchy(in:afterScreenUpdates:) method instead.

## See Also

### Capturing a view snapshot

func resizableSnapshotView(from: CGRect, afterScreenUpdates: Bool, withCapInsets: UIEdgeInsets) -> UIView?

Returns a snapshot view based on the specified contents of the current view, with stretchable insets.

func drawHierarchy(in: CGRect, afterScreenUpdates: Bool) -> Bool

Renders a snapshot of the complete view hierarchy as visible onscreen into the current context.

