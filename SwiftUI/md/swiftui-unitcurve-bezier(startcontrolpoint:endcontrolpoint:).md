

- SwiftUI
- UnitCurve
-  bezier(startControlPoint:endControlPoint:) 

Type Method

# bezier(startControlPoint:endControlPoint:)

Creates a new curve using bezier control points.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
static func bezier(
    startControlPoint: UnitPoint,
    endControlPoint: UnitPoint
) -> UnitCurve
```

## Parameters 

`startControlPoint`  

The cubic Bézier control point associated with the curve’s start point at (0, 0). The tangent vector from the start point to its control point defines the initial velocity of the timing function.

`endControlPoint`  

The cubic Bézier control point associated with the curve’s end point at (1, 1). The tangent vector from the end point to its control point defines the final velocity of the timing function.

## Discussion

The x components of the control points are clamped to the range \[0,1\] when the curve is evaluated.

