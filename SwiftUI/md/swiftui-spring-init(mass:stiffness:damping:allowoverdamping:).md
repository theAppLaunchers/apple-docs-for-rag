

- SwiftUI
- Spring
-  init(mass:stiffness:damping:allowOverDamping:) 

Initializer

# init(mass:stiffness:damping:allowOverDamping:)

Creates a spring with the specified mass, stiffness, and damping.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
init(
    mass: Double = 1.0,
    stiffness: Double,
    damping: Double,
    allowOverDamping: Bool = false
)
```

## Parameters 

`mass`  

Specifies that property of the object attached to the end of the spring.

`stiffness`  

The corresponding spring coefficient.

`damping`  

Defines how the spring’s motion should be damped due to the forces of friction.

## See Also

### Creating a spring

init(duration: TimeInterval, bounce: Double)

Creates a spring with the specified duration and bounce.

init(response: Double, dampingRatio: Double)

Creates a spring with the specified response and damping ratio.

init(settlingDuration: TimeInterval, dampingRatio: Double, epsilon: Double)

Creates a spring with the specified duration and damping ratio.

