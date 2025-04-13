

- SpriteKit
- SKPhysicsBody
-  contactTestBitMask 

Instance Property

# contactTestBitMask

A mask that defines which categories of physics bodies cause intersection notifications with this physics body.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
var contactTestBitMask: UInt32 { get set }
```

## Discussion

When two bodies share the same space, each body’s category mask is tested against the other body’s contact mask by performing a logical AND operation. If either comparison results in a nonzero value, an SKPhysicsContact object is created and passed to the physics world’s delegate. For best performance, only set bits in the contacts mask for interactions you are interested in.

The default value is `0x00000000` (all bits cleared).

## See Also

### Working with Collisions and Contacts

About Collisions and Contacts

Learn how to set up nodes for collision detection.

var categoryBitMask: UInt32

A mask that defines which categories this physics body belongs to.

var collisionBitMask: UInt32

A mask that defines which categories of physics bodies can collide with this physics body.

var usesPreciseCollisionDetection: Bool

A Boolean value that determines whether the physics world uses an iterative collision detection algorithm.

func allContactedBodies() -> [SKPhysicsBody]

The physics bodies that this physics body is in contact with.

