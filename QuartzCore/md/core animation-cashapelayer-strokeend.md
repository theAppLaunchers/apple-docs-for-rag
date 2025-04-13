

- Core Animation
- CAShapeLayer
-  strokeEnd 

Instance Property

# strokeEnd

The relative location at which to stop stroking the path. Animatable.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.1+macOS 10.6+tvOS 9.0+visionOS 1.0+

``` source
var strokeEnd: CGFloat { get set }
```

## Discussion

The value of this property must be in the range 0.0 to 1.0. The default value of this property is 1.0.

Combined with the strokeStart property, this property defines the subregion of the path to stroke. The value in this property indicates the relative point along the path at which to finish stroking while the strokeStart property defines the starting point. A value of 0.0 represents the beginning of the path while a value of 1.0 represents the end of the path. Values in between are interpreted linearly along the path length.

## See Also

### Accessing Shape Style Properties

var fillColor: CGColor?

The color used to fill the shape’s path. Animatable.

var fillRule: CAShapeLayerFillRule

The fill rule used when filling the shape’s path.

var lineCap: CAShapeLayerLineCap

Specifies the line cap style for the shape’s path.

var lineDashPattern: [NSNumber]?

The dash pattern applied to the shape’s path when stroked.

var lineDashPhase: CGFloat

The dash phase applied to the shape’s path when stroked. Animatable.

var lineJoin: CAShapeLayerLineJoin

Specifies the line join style for the shape’s path.

var lineWidth: CGFloat

Specifies the line width of the shape’s path. Animatable.

var miterLimit: CGFloat

The miter limit used when stroking the shape’s path. Animatable.

var strokeColor: CGColor?

The color used to stroke the shape’s path. Animatable.

var strokeStart: CGFloat

The relative location at which to begin stroking the path. Animatable.

