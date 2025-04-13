

- UIKit
- UIView
-  anchorPoint 

Instance Property

# anchorPoint

The anchor point of the view’s bounds rectangle.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+tvOS 16.0+visionOS 1.0+

``` source
@MainActor
var anchorPoint: CGPoint { get set }
```

## Discussion

You specify the value for this property using the unit coordinate space, where (`0`, `0`) is the bottom-left corner of the view’s bounds rectangle, and (`1`, `1`) is the top-right corner. The default value of this property is (`0.5`, `0.5`), which represents the center of the view’s bounds rectangle.

All geometric manipulations to the view occur about the specified point. For example, applying a rotation transform to a view with the default anchor point causes the view to rotate around its center. Changing the anchor point to a different location causes the view to rotate around that new point.

## See Also

### Configuring the bounds and frame rectangles

var frame: CGRect

The frame rectangle, which describes the view’s location and size in its superview’s coordinate system.

var bounds: CGRect

The bounds rectangle, which describes the view’s location and size in its own coordinate system.

var center: CGPoint

The center point of the view’s frame rectangle.

var transform: CGAffineTransform

Specifies the transform applied to the view, relative to the center of its bounds.

var transform3D: CATransform3D

The three-dimensional transform to apply to the view.

