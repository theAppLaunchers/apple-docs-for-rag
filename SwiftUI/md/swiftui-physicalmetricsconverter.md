

- SwiftUI
-  PhysicalMetricsConverter 

Structure

# PhysicalMetricsConverter

A physical metrics converter provides conversion between point values and their extent in 3D space, in the form of physical length measurements.

visionOS 1.0+

``` source
@MainActor @preconcurrency
struct PhysicalMetricsConverter
```

## Overview

Converters are available from the environment of a `View` or other type that inherits a `View`‘s environments, and are associated with the scene that contains that environment. The conversions expect (or emit) values in points in that scene’s coordinate system, and convert these to (or from) measurements of length in the user’s or scene’s reference frame.

To obtain a converter, use the physicalMetrics key:

```
struct MyView: View {
    @Environment(\.physicalMetrics) var physicalMetrics
    …
}
```

When user action modifies a scene so that measurements have changed (e.g., by changing its scale), the view that accessed that environment key and its hierarchy will be reevaluated.

Attempting to obtain a converter inside a type not associated with a scene’s contents (for example, from an App or Scene’s environment) is not supported.

## Compensating for World Scaling

By default in apps linked against the visionOS 2.0 SDK or later, these conversions match the scene’s coordinate system, including any scale applied to it by the system. If you’re using meters as the unit, this will match the notion of meters in an unscaled `RealityView` in the same scene.

To obtain measurements that are accurate to the user’s surroundings, use the worldScalingCompensation(_:) method to enable an appropriate compensation mode for the scale.

## Topics

### Converting a unit length

func convert(_:from:)

Converts a length in the specified unit to a length in points suitable for use in the environment this converter is associated with.

func convert(_:to:)

Converts a point’s coordinates to physical length measurements in the specified unit.

### Instance Properties

var worldScalingCompensation: WorldScalingCompensation

Provides the current world scale compensation of this converter.

### Instance Methods

func worldScalingCompensation(WorldScalingCompensation) -> PhysicalMetricsConverter

Obtains a new converter with a different world scale compensation behavior.

## Relationships

### Conforms To

- Equatable
- Sendable

## See Also

### Measuring a view

struct GeometryReader

A container view that defines its content as a function of its own size and coordinate space.

struct GeometryReader3D

A container view that defines its content as a function of its own size and coordinate space.

struct GeometryProxy

A proxy for access to the size and coordinate space (for anchor resolution) of the container view.

struct GeometryProxy3D

A proxy for access to the size and coordinate space of the container view.

func coordinateSpace(NamedCoordinateSpace) -> some View

Assigns a name to the view’s coordinate space, so other code can operate on dimensions like points and sizes relative to the named space.

enum CoordinateSpace

A resolved coordinate space created by the coordinate space protocol.

protocol CoordinateSpaceProtocol

A frame of reference within the layout system.

struct PhysicalMetric

Provides access to a value in points that corresponds to the specified physical measurement.

