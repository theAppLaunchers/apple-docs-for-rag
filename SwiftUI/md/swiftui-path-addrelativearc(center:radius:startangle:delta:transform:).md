

- SwiftUI
- Path
-  addRelativeArc(center:radius:startAngle:delta:transform:) 

Instance Method

# addRelativeArc(center:radius:startAngle:delta:transform:)

Adds an arc of a circle to the path, specified with a radius and a difference in angle.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
mutating func addRelativeArc(
    center: CGPoint,
    radius: CGFloat,
    startAngle: Angle,
    delta: Angle,
    transform: CGAffineTransform = .identity
)
```

## Parameters 

`center`  

The center of the arc, in user space coordinates.

`radius`  

The radius of the arc, in user space coordinates.

`startAngle`  

The angle to the starting point of the arc, measured from the positive x-axis.

`delta`  

The difference between the starting angle and ending angle of the arc. A positive value creates a counter- clockwise arc (in user space coordinates), and vice versa.

`transform`  

An affine transform to apply to the arc before adding to the path. Defaults to the identity transform if not specified. /

## Discussion

This method calculates starting and ending points using the radius and angles you specify, uses a sequence of cubic Bézier curves to approximate a segment of a circle between those points, and then appends those curves to the path.

The `delta` parameter determines both the length of the arc the direction in which the arc is created; the actual direction of the final path is dependent on the `transform` parameter and the current transform of a context where the path is drawn. However, because SwiftUI by default uses a vertically-flipped coordinate system (with the origin in the top-left of the view), specifying a clockwise arc results in a counterclockwise arc after the transformation is applied.

If the path ends with an unclosed subpath, this method adds a line connecting the current point to the starting point of the arc. If there is no unclosed subpath, this method creates a new subpath whose starting point is the starting point of the arc. The ending point of the arc becomes the new current point of the path.

## See Also

### Drawing a path

func move(to: CGPoint)

Begins a new subpath at the specified point.

func addArc(center: CGPoint, radius: CGFloat, startAngle: Angle, endAngle: Angle, clockwise: Bool, transform: CGAffineTransform)

Adds an arc of a circle to the path, specified with a radius and angles.

func addArc(tangent1End: CGPoint, tangent2End: CGPoint, radius: CGFloat, transform: CGAffineTransform)

Adds an arc of a circle to the path, specified with a radius and two tangent lines.

func addCurve(to: CGPoint, control1: CGPoint, control2: CGPoint)

Adds a cubic Bézier curve to the path, with the specified end point and control points.

func addEllipse(in: CGRect, transform: CGAffineTransform)

Adds an ellipse that fits inside the specified rectangle to the path.

func addLine(to: CGPoint)

Appends a straight line segment from the current point to the specified point.

func addLines([CGPoint])

Adds a sequence of connected straight-line segments to the path.

func addPath(Path, transform: CGAffineTransform)

Appends another path value to this path.

func addQuadCurve(to: CGPoint, control: CGPoint)

Adds a quadratic Bézier curve to the path, with the specified end point and control point.

func addRect(CGRect, transform: CGAffineTransform)

Adds a rectangular subpath to the path.

func addRects([CGRect], transform: CGAffineTransform)

Adds a set of rectangular subpaths to the path.

func addRoundedRect(in: CGRect, cornerSize: CGSize, style: RoundedCornerStyle, transform: CGAffineTransform)

Adds a rounded rectangle to the path.

func closeSubpath()

Closes and completes the current subpath.

