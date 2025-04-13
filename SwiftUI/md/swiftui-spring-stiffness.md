

- SwiftUI
- Spring
-  stiffness 

Instance Property

# stiffness

The spring stiffness coefficient.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
var stiffness: Double { get }
```

## Discussion

Increasing the stiffness reduces the number of oscillations and will reduce the settling duration. Decreasing the stiffness increases the the number of oscillations and will increase the settling duration.

## See Also

### Getting spring characteristics

var bounce: Double

How bouncy the spring is.

var damping: Double

Defines how the spring’s motion should be damped due to the forces of friction.

var dampingRatio: Double

The amount of drag applied, as a fraction of the amount needed to produce critical damping.

var duration: TimeInterval

The perceptual duration, which defines the pace of the spring.

var mass: Double

The mass of the object attached to the end of the spring.

var response: Double

The stiffness of the spring, defined as an approximate duration in seconds.

var settlingDuration: TimeInterval

The estimated duration required for the spring system to be considered at rest.

