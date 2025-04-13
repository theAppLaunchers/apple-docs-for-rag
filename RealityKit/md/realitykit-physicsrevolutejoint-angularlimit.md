

- RealityKit
- PhysicsRevoluteJoint
-  angularLimit 

Instance Property

# angularLimit

A limit of the rotational freedom between the pins around the x-axis.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
var angularLimit: ClosedRange?
```

## Discussion

If defined, this limits the rotation of pin1 around the x-axis of pin0. There is no limit if this property is `nil`.

