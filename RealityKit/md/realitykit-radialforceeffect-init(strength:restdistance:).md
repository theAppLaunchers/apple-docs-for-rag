

- RealityKit
- RadialForceEffect
-  init(strength:restDistance:) 

Initializer

# init(strength:restDistance:)

Creates a radial force effect.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
init(
    strength: Double,
    restDistance: Double
)
```

## Parameters 

`strength`  

The magnitude of the spring effect—a larger strength simulates a stiffer spring.

`restDistance`  

Objects at this distance will receive zero radial force. Otherwise they will gravitate toward this distance along the radial direction. Objects will be attracted to the origin directly if this property is set to zero.

