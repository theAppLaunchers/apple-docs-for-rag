

- AppKit
- NSView
-  setContentCompressionResistancePriority(\_:for:) 

Instance Method

# setContentCompressionResistancePriority(\_:for:)

Sets the priority with which a view resists being made smaller than its intrinsic size.

macOS 10.7+

``` source
@MainActor
func setContentCompressionResistancePriority(
    _ priority: NSLayoutConstraint.Priority,
    for orientation: NSLayoutConstraint.Orientation
)
```

## Parameters 

`priority`  

The new priority.

`orientation`  

The orientation for which the compression resistance priority should be set.

## Discussion

Custom views should set default values for both orientations on creation, based on their content, typically to defaultLow or defaultHigh. When creating user interfaces, the layout designer can modify these priorities for specific views when the overall layout design requires different tradeoffs than the natural priorities of the views being used in the interface.

Subclasses should not override this method.

## See Also

### Measuring in Auto Layout

var fittingSize: NSSize

The minimum size of the view that satisfies the constraints it holds.

var intrinsicContentSize: NSSize

The natural size for the receiving view, considering only properties of the view itself.

func invalidateIntrinsicContentSize()

Invalidates the view’s intrinsic content size.

func contentCompressionResistancePriority(for: NSLayoutConstraint.Orientation) -> NSLayoutConstraint.Priority

Returns the priority with which a view resists being made smaller than its intrinsic size.

func contentHuggingPriority(for: NSLayoutConstraint.Orientation) -> NSLayoutConstraint.Priority

Returns the priority with which a view resists being made larger than its intrinsic size.

func setContentHuggingPriority(NSLayoutConstraint.Priority, for: NSLayoutConstraint.Orientation)

Sets the priority with which a view resists being made larger than its intrinsic size.

class let noIntrinsicMetric: CGFloat

A value that tells the layout system to ignore the intrinsic size value for a given dimension.

