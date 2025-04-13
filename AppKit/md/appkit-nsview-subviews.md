

- AppKit
- NSView
-  subviews 

Instance Property

# subviews

The array of views embedded in the current view.

macOS

``` source
@MainActor
var subviews: [NSView] { get set }
```

## Discussion

This array contains zero or more `NSView` objects that represent the views embedded in the current view’s content. The current view acts as the superview for each subview. The order of the subviews may be considered as being back-to-front, but this does not imply invalidation and drawing behavior.

When loading a view from a nib or storyboard file, the order of subviews is determined by the nib or storyboard file itself and usually corresponds to the order in which the views were added. Similarly, when adding subviews programmatically, the order is based on the order in which you added them.

When performing hit-test operations on a view, you should start at the last view in this array and work backwards.

Set this property to reorder the view’s existing subviews, add or remove subviews en masse, replace all of the view’s subviews with a new set of subviews, or remove all the view’s subviews. When you assign a valid, new array of subviews, the system performs required sorting and sends addSubview(_:) and removeFromSuperview() messages as necessary to leave the property with the requested new array.  Any member of the new array that isn’t already a subview of the view is added.  Any member of the view’s existing `subviews` array that isn’t in the new array is removed.  Any views that are in both subviews and the new array are moved in the subviews array as needed, without being removed and re-added.

This property marks the affected view and window areas as needing display.

Note

The contents of this array may change at any time. If you intend to manipulate the contents of the array, work off a copy of the array.

## See Also

### Related Documentation

func addSubview(NSView, positioned: NSWindow.OrderingMode, relativeTo: NSView?)

Inserts a view among the view’s subviews so it’s displayed immediately above or below another view.

func addSubview(NSView)

Adds a view to the view’s subviews so it’s displayed above its siblings.

func removeFromSuperview()

Unlinks the view from its superview and its window, removes it from the responder chain, and invalidates its cursor rectangles.

### Getting the Related Objects

var superview: NSView?

The view that is the parent of the current view.

var window: NSWindow?

The view’s window object, if it is installed in a window.

var opaqueAncestor: NSView?

The view’s closest opaque ancestor, which might be the view itself.

func isDescendant(of: NSView) -> Bool

Returns a Boolean value that indicates whether the view is a subview of the specified view.

func ancestorShared(with: NSView) -> NSView?

Returns the closest ancestor shared by the view and another specified view.

var enclosingMenuItem: NSMenuItem?

The menu item containing the view or any of its superviews in the view hierarchy.

var enclosingScrollView: NSScrollView?

The nearest ancestor scroll view that contains the current view.

