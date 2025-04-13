

- SpriteKit
- SKAction
-  applyImpulse(\_:duration:) 

Type Method

# applyImpulse(\_:duration:)

Creates an action that applies an impulse to the center of gravity of a physics body.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
class func applyImpulse(
    _ impulse: CGVector,
    duration: TimeInterval
) -> SKAction
```

## Parameters 

`impulse`  

A vector that describes how much momentum to impart to the body in each dimension over the duration of the action. The impulse is measured in Newton-seconds.

`duration`  

The duration over which the total impulse should be applied to the physics body.

## Return Value

A new action object.

## Discussion

When the action executes, applies a constant force to the physics body for the duration of the action. The force is calculated by dividing the impulse strength by the duration of the action. For example, if an impulse of `1` Newton-second is applied to the physics body, and the the duration is `10` seconds, then a force of `0.1` Newtons is applied to the physics body.

This action is reversible; it applies an equal impulse in the opposite direction.

## See Also

### Animating Properties of a Node’s Physics Body

class func applyForce(CGVector, duration: TimeInterval) -> SKAction

Creates an action that applies a force to the center of gravity of a node’s physics body.

class func applyTorque(CGFloat, duration: TimeInterval) -> SKAction

Creates an action that applies a torque to a node’s physics body.

class func applyForce(CGVector, at: CGPoint, duration: TimeInterval) -> SKAction

Creates an action that applies a force to a specific point on a node’s physics body.

class func applyAngularImpulse(CGFloat, duration: TimeInterval) -> SKAction

Creates an action that applies an angular impulse to a node’s physics body.

class func applyImpulse(CGVector, at: CGPoint, duration: TimeInterval) -> SKAction

Creates an action that applies an impulse to a specific point of a node’s physics body.

class func changeCharge(to: Float, duration: TimeInterval) -> SKAction

Creates an action that changes the charge of a node’s physics body to a new value.

class func changeCharge(by: Float, duration: TimeInterval) -> SKAction

Creates an action that changes the charge of a node’s physics body by a relative value.

class func changeMass(to: Float, duration: TimeInterval) -> SKAction

Creates an action that changes the mass of a node’s physics body to a new value.

class func changeMass(by: Float, duration: TimeInterval) -> SKAction

Creates an action that changes the mass of a node’s physics body by a relative value.

class func strength(to: Float, duration: TimeInterval) -> SKAction

Creates an action that animates a change of a physics field’s strength.

class func strength(by: Float, duration: TimeInterval) -> SKAction

Creates an action that animates a change of a physics field’s strength to a value relative to the existing value.

class func falloff(to: Float, duration: TimeInterval) -> SKAction

Creates an action that animates a change of a physics field’s falloff.

class func falloff(by: Float, duration: TimeInterval) -> SKAction

Creates an action that animates a change of a physics field’s falloff to a value relative to the existing value.

