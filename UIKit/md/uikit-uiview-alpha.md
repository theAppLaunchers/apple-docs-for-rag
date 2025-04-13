

- UIKit
- UIView
-  alpha 

Instance Property

# alpha

The view’s alpha value.

iOSiPadOSMac CatalysttvOSvisionOS

``` source
@MainActor
var alpha: CGFloat { get set }
```

## Mentioned in 

Configuring the cells for your table

## Discussion

The value of this property is a floating-point number in the range `0.0` to `1.0`, where `0.0` represents totally transparent and `1.0` represents totally opaque. Changing the value of this property updates the alpha value of the current view only. However, the transparency imparted by that alpha value affects all of the view’s contents, including its subviews. For example, a subview with an alpha value of `1.0` that is embedded in a parent view with an alpha value of `0.5,` appears onscreen as if its alpha value is also `0.5`.

Changes to this property can be animated.

## See Also

### Configuring a view’s visual appearance

var backgroundColor: UIColor?

The view’s background color.

var isHidden: Bool

A Boolean value that determines whether the view is hidden.

var isOpaque: Bool

A Boolean value that determines whether the view is opaque.

var tintColor: UIColor!

The first nondefault tint color value in the view’s hierarchy, ascending from and starting with the view itself.

var tintAdjustmentMode: UIView.TintAdjustmentMode

The first non-default tint adjustment mode value in the view’s hierarchy, ascending from and starting with the view itself.

var clipsToBounds: Bool

A Boolean value that determines whether subviews are confined to the bounds of the view.

var clearsContextBeforeDrawing: Bool

A Boolean value that determines whether the view’s bounds should be automatically cleared before drawing.

var mask: UIView?

An optional view whose alpha channel is used to mask a view’s content.

class var layerClass: AnyClass

Returns the class used to create the layer for instances of this class.

var layer: CALayer

The view’s Core Animation layer to use for rendering.

