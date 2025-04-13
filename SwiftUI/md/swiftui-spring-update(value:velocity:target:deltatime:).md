

- SwiftUI
- Spring
-  update(value:velocity:target:deltaTime:) 

Instance Method

# update(value:velocity:target:deltaTime:)

Updates the current value and velocity of a spring.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
func update(
    value: inout V,
    velocity: inout V,
    target: V,
    deltaTime: TimeInterval
) where V : VectorArithmetic
```

## Parameters 

`value`  

The current value of the spring.

`velocity`  

The current velocity of the spring.

`target`  

The target that `value` is moving towards.

`deltaTime`  

The amount of time that has passed since the spring was at the position specified by `value`.

