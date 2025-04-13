

- SceneKit
- SCNPhysicsContact
-  collisionImpulse 

Instance Property

# collisionImpulse

The force over time of the collision, in newton-seconds.

iOSiPadOSMac Catalyst 13.1+macOS 10.10+tvOSvisionOSwatchOS

``` source
var collisionImpulse: CGFloat { get }
```

## Discussion

This property’s value tells you how hard the bodies struck each other in a collision. For example, in a game you might allow a character to proceed unhindered after a minor collision, but take damage when struck with sufficient force.

## See Also

### Inspecting the Contact Properties

var nodeA: SCNNode

The node containing the first body in the contact.

var nodeB: SCNNode

The node containing the second body in the contact.

var contactPoint: SCNVector3

The contact point between the two physics bodies, in scene coordinates.

var contactNormal: SCNVector3

The normal vector at the contact point between the two physics bodies, in scene coordinates.

var penetrationDistance: CGFloat

The distance of overlap, in units of scene coordinate space, between the two physics bodies.

