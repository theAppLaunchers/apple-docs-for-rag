

- UIKit
- UIView
-  frame 

Instance Property

# frame

The frame rectangle, which describes the view’s location and size in its superview’s coordinate system.

iOSiPadOSMac CatalysttvOSvisionOS

``` source
@MainActor
var frame: CGRect { get set }
```

## Discussion

This rectangle defines the size and position of the view in its superview’s coordinate system. Use this rectangle during layout operations to set the size and position the view. Setting this property changes the point specified by the center property and changes the size in the bounds rectangle accordingly. The coordinates of the frame rectangle are always specified in points.

Warning

If the transform property is not the identity transform, the value of this property is undefined and therefore should be ignored.

Changing the frame rectangle automatically redisplays the view without calling its draw(_:) method. If you want UIKit to call the draw(_:) method when the frame rectangle changes, set the contentMode property to UIView.ContentMode.redraw.

Changes to this property can be animated. However, if the transform property contains a non-identity transform, the value of the frame property is undefined and should not be modified. In that case, reposition the view using the center property and adjust the size using the bounds property instead.

## See Also

### Configuring the bounds and frame rectangles

var bounds: CGRect

The bounds rectangle, which describes the view’s location and size in its own coordinate system.

var center: CGPoint

The center point of the view’s frame rectangle.

var transform: CGAffineTransform

Specifies the transform applied to the view, relative to the center of its bounds.

var transform3D: CATransform3D

The three-dimensional transform to apply to the view.

var anchorPoint: CGPoint

The anchor point of the view’s bounds rectangle.

