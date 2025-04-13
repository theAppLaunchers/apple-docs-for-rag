

- SceneKit
- SCNPhysicsWorld
-  gravity 

Instance Property

# gravity

A vector that specifies the gravitational acceleration applied to physics bodies in the physics world.

iOSiPadOSMac Catalyst 13.1+macOS 10.10+tvOSvisionOSwatchOS

``` source
var gravity: SCNVector3 { get set }
```

## Discussion

The components of this vector are measured in meters per second per second. The default value is `(0.0,-9.8,0.0)`.

This property applies a constant acceleration to all physics bodies in the world, simulating the effect of gravity near the surface of the Earth. For more sophisticated gravity effects, including limited areas of effect and strength proportional to distance, use the SCNPhysicsField class. When using fields, you may want to set this property to the zero vector so that fields provide all gravity effects in the physics world.

## See Also

### Managing the Physics Simulation

var speed: CGFloat

The rate at which the simulation executes.

var timeStep: TimeInterval

The time interval between updates to the physics simulation.

func updateCollisionPairs()

Forces the physics engine to reevaluate possible collisions between physics bodies.

