

- Core Animation
- CAKeyframeAnimation
-  continuityValues 

Instance Property

# continuityValues

An array of numbers that define the sharpness of the timing curve’s corners.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+

``` source
var continuityValues: [NSNumber]? { get set }
```

## Discussion

This property is an array of NSNumber objects, used only for the cubic calculation modes. Positive values result in sharper corners while negative values create inverted corners. The first value defines the behavior of the tangent to the first control point, the second value controls the second point’s tangents, and so on. If you do not specify a value for a given control point, the value `0` is used.

## See Also

### Cubic Mode Attributes

var tensionValues: [NSNumber]?

An array of numbers that define the tightness of the curve.

var biasValues: [NSNumber]?

An array of numbers that define the position of the curve relative to a control point.

