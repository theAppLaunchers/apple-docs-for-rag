

- AppKit
- NSStackView
-  setHuggingPriority(\_:for:) 

Instance Method

# setHuggingPriority(\_:for:)

Sets the Auto Layout priority for the stack view to minimize its size, for a specified user interface axis.

macOS 10.9+

``` source
@MainActor
func setHuggingPriority(
    _ huggingPriority: NSLayoutConstraint.Priority,
    for orientation: NSLayoutConstraint.Orientation
)
```

## Parameters 

`huggingPriority`  

The Auto Layout priority for the stack view to minimize its size. The default value is defaultLow. Other valid values are those in the NSLayoutConstraint.Priority enumeration.

`orientation`  

The horizontal or vertical user interface axis for which you’re setting the stack view’s hugging priority; one of the constants from the NSUserInterfaceLayoutOrientation enumeration.

- To specify horizontal-axis hugging for any stack view (whether it uses vertical or horizontal layout), use the NSUserInterfaceLayoutOrientation.horizontal constant.

- To specify vertical-axis hugging for any stack view (whether it uses vertical or horizontal layout), use the NSUserInterfaceLayoutOrientation.vertical constant.

## Discussion

This method lets you specify a different hugging priority for each user interface axis. The default value for hugging priority, on both user interface axes, is defaultLow. If you have not added constraints between the stack view and its enclosing view, the stack view stays as small as possible to fully contain its views—independent of the size of the view that contains it.

To configure a stack view to grow and shrink according to the size of its enclosing view, add constraints between the stack view and its enclosing view by using Auto Layout priorities higher than the hugging priority.

To configure a stack view to prevent its enclosing view from growing, use priorities for the constraints between the stack view and its enclosing view that are lower than the hugging priority.

The value of the hugging priority also affects spacing between views and between gravity areas, as described in the discussion for the spacing property.

Note

The hugging priority for a stack view behaves differently than the content hugging priority for a generic view as configured with the NSView method setContentHuggingPriority(_:for:). A stack view has no intrinsic content size and does not have a configurable content compression resistance. Calling the setContentCompressionResistancePriority(_:for:) method on a stack view has no effect.

## See Also

### Related Documentation

func huggingPriority(for: NSLayoutConstraint.Orientation) -> NSLayoutConstraint.Priority

Returns the Auto Layout priority for the stack view to minimize its size to fit its contained views as closely as possible, for a specified user interface axis.

### Configuring Dynamic Behavior for a Stack View

var detachesHiddenViews: Bool

A Boolean value that indicates whether the stack view removes hidden views from its view hierarchy.

func setClippingResistancePriority(NSLayoutConstraint.Priority, for: NSLayoutConstraint.Orientation)

Sets the Auto Layout priority for resisting clipping of views in the stack view when Auto Layout attempts to reduce the stack view’s size.

