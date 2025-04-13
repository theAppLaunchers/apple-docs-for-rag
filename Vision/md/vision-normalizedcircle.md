

- Vision
-  NormalizedCircle 

Structure

# NormalizedCircle

The center point and radius of a 2D circle.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+

``` source
struct NormalizedCircle
```

## Topics

### Creating a normalized circle

init(center: NormalizedPoint, radius: CGFloat)

Creates a circle with the specified center and radius.

static var zero: NormalizedCircle

A circle object centered at the origin, with a radius of zero.

### Inspecting a normalized circle

let center: NormalizedPoint

The circle’s center point.

let radius: CGFloat

The circle’s radius.

### Determining whether the circle contains a point

func contains(NormalizedPoint) -> Bool

Returns a Boolean value that indicates whether this circle, including its boundary, contains the specified point.

func contains(NormalizedPoint, inCircumferentialRingOfWidth: CGFloat) -> Bool

Returns a Boolean value that indicates whether a ring around this circle’s circumference contains the specified point.

### Getting the bounding circle

static func boundingCircle(for: [NormalizedPoint]) -> NormalizedCircle

Creates the smallest circle that encloses the points you specify.

## See Also

### Coordinate conversion

struct NormalizedPoint

A point in a 2D coordinate system.

struct NormalizedRect

The location and dimensions of a rectangle.

enum CoordinateOrigin

The origin of a coordinate system relative to an image.

