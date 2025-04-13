

- UIKit
- UIView
-  setNeedsLayout() 

Instance Method

# setNeedsLayout()

Invalidates the current layout of the receiver and triggers a layout update during the next update cycle.

iOSiPadOSMac CatalysttvOSvisionOS

``` source
@MainActor
func setNeedsLayout()
```

## Discussion

Call this method on your application’s main thread when you want to adjust the layout of a view’s subviews. This method makes a note of the request and returns immediately. Because this method does not force an immediate update, but instead waits for the next update cycle, you can use it to invalidate the layout of multiple views before any of those views are updated. This behavior allows you to consolidate all of your layout updates to one update cycle, which is usually better for performance.

## See Also

### Laying out subviews

func layoutSubviews()

Lays out subviews.

func layoutIfNeeded()

Lays out the subviews immediately, if layout updates are pending.

class var requiresConstraintBasedLayout: Bool

A Boolean value that indicates whether the receiver depends on the constraint-based layout system.

var translatesAutoresizingMaskIntoConstraints: Bool

A Boolean value that determines whether the view’s autoresizing mask is translated into Auto Layout constraints.

