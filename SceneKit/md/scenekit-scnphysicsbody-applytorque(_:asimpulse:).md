

- SceneKit
- SCNPhysicsBody
-  applyTorque(\_:asImpulse:) 

Instance Method

# applyTorque(\_:asImpulse:)

Applies a net torque or a change in angular momentum to the body.

iOSiPadOSMac Catalyst 13.1+macOS 10.10+tvOSvisionOSwatchOS

``` source
func applyTorque(
    _ torque: SCNVector4,
    asImpulse impulse: Bool
)
```

## Parameters 

`torque`  

The direction and magnitude of the torque (in newton-meters) or of the change of angular momentum (in newton-meter-seconds), relative to the world coordinate space of the scene.

`impulse`  

true to apply an instantaneous change in angular momentum; false to apply a torque that affects the body at the end of the simulation step.

## Discussion

Applying a torque to a body changes its angular velocity by an amount related to its mass and shape, rotating it without affecting its linear acceleration. Each component of the torque vector relates to rotation about the corresponding axis in the local coordinate system of the SCNNode object containing the physics body. For example, applying a torque of `{0.0, 0.0, 1.0}` causes a node to spin counterclockwise around the world-space z-axis.

The `impulse` parameter determines how this method contributes to the physics simulation:

- If you specify true, SceneKit treats the `direction` parameter as an instantaneous change in angular momentum, measured in newton-meter-seconds.

- If you specify false, SceneKit treats the `direction` parameter as a torque, measured in newton-meters. At the end of each simulation step (by default, a step occurs once for each frame in the rendering loop), SceneKit sums all forces and torques applied to the physics body during that step and accelerates the body according to the net effect of those forces and torques. Use this option when you want to simulate gradual acceleration by calling applyTorque(_:asImpulse:) on each simulation step.

Note

The `impulse` parameter effectively changes the unit of magnitude. A value that results in a certain acceleration when applied continuously on each frame of the simulation results in much less acceleration if applied only during a single frame.

As with all physical quantities in SceneKit, you need not use realistic force and torque measurements in your app—the effects of the physics simulation depend on the relative differences between forces, not on their absolute values. You may use whatever values produce the behavior or gameplay you’re looking for as long as you use them consistently.

## See Also

### Applying Forces, Impulses, and Torques

func applyForce(SCNVector3, asImpulse: Bool)

Applies a force or impulse to the body at its center of mass.

func applyForce(SCNVector3, at: SCNVector3, asImpulse: Bool)

Applies a force or impulse to the body at a specific point.

func clearAllForces()

Cancels all continuous forces and torques acting on the physics body during the current simulation step.

