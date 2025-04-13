

- RealityKit
- OrbitAnimation
-  blendLayer 

Instance Property

# blendLayer

The order in which the framework composites the animation.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+visionOS

``` source
var blendLayer: Int32 { get set }
```

## Discussion

The framework applies multiple animations on the same target in ascending order of this property’s value. Animations in a lower layer run before animations in a higher layer. Animations that share the same value apply in the order that they execute.

## See Also

### Configuring the animation

var startTransform: Transform

The pose of the orbiting object at the start of the animation.

var axis: SIMD3&lt;Float>

A 3D vector that points in the direction of the axis around which to rotate.

var name: String

A textual name for the animation.

var bindTarget: BindTarget

A textual name that identifies the particular property that animates.

var rotationCount: Float

The number of times to rotate the target entity before stopping.

var spinClockwise: Bool

A Boolean value that indicates whether the object orbits the center point in the clockwise direction.

var orientToPath: Bool

A Boolean value that indicates whether the orbiting object updates its orientation during the animation to orient itself along the rotation path.

var additive: Bool

A Boolean value that indicates whether the animation builds on the current state of the target entity or resets the state before running.

