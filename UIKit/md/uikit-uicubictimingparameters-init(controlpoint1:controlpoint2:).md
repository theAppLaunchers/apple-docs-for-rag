

- UIKit
- UICubicTimingParameters
-  init(controlPoint1:controlPoint2:) 

Initializer

# init(controlPoint1:controlPoint2:)

Initializes the object with the specified control points for a cubic Bézier curve.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+tvOS 10.0+visionOS 1.0+

``` source
@MainActor
init(
    controlPoint1 point1: CGPoint,
    controlPoint2 point2: CGPoint
)
```

## Parameters 

`point1`  

The first control point for the cubic Bézier timing curve. The x and y values of this point must be in the range `0.0` to `1.0`.

`point2`  

The second control point for the cubic Bézier timing curve. The x and y values of this point must be in the range `0.0` to `1.0`.

## Return Value

An initialized timing parameter object or `nil` if the object could not be created.

## Discussion

Use this method to initialize the timing curve with a custom cubic Bézier curve. The curve consists of a line whose starting point is (0, 0), whose end point is (1, 1), and whose shape is defined by `point1` and `point2`.

## See Also

### Initializing a cubic timing parameters object

init()

Initializes the object with the system’s default timing curve.

init(animationCurve: UIView.AnimationCurve)

Initializes the object with the specified UIKit timing curve.

init?(coder: NSCoder)

Creates a timing parameters object from data in an unarchiver.

