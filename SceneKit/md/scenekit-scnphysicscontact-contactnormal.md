

- SceneKit
- SCNPhysicsContact
-  contactNormal 

Instance Property

# contactNormal

The normal vector at the contact point between the two physics bodies, in scene coordinates.

iOSiPadOSMac Catalyst 13.1+macOS 10.10+tvOSvisionOSwatchOS

``` source
var contactNormal: SCNVector3 { get }
```

## Discussion

This vector tells you which direction the bodies were moving relative to one another at the time of the collision. For example, in a game you can examine this vector to have enemy characters take damage when struck from above by the player character but damage the player character instead when they collide side-to-side.

## See Also

### Inspecting the Contact Properties

var nodeA: SCNNode

The node containing the first body in the contact.

var nodeB: SCNNode

The node containing the second body in the contact.

var contactPoint: SCNVector3

The contact point between the two physics bodies, in scene coordinates.

var collisionImpulse: CGFloat

The force over time of the collision, in newton-seconds.

var penetrationDistance: CGFloat

The distance of overlap, in units of scene coordinate space, between the two physics bodies.

