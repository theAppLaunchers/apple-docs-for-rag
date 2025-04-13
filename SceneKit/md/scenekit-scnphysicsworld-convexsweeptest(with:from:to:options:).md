

- SceneKit
- SCNPhysicsWorld
-  convexSweepTest(with:from:to:options:) 

Instance Method

# convexSweepTest(with:from:to:options:)

Searches for physics bodies in the space formed by moving a convex shape through the physics world.

iOSiPadOSMac Catalyst 13.1+macOS 10.10+tvOSvisionOSwatchOS

**macOS**

``` source
func convexSweepTest(
    with shape: SCNPhysicsShape,
    from: SCNMatrix4,
    to: SCNMatrix4,
    options: [SCNPhysicsWorld.TestOption : Any]? = nil
) -> [SCNPhysicsContact]
```

**iOS, iPadOS, Mac Catalyst, tvOS, visionOS, watchOS**

``` source
func convexSweepTest(
    with shape: SCNPhysicsShape,
    from: SCNMatrix4,
    to: SCNMatrix4,
    options: [SCNPhysicsWorld.TestOption : Any]? = nil
) -> [SCNPhysicsContact]
```

## Parameters 

`shape`  

A physics shape. This shape must enclose a convex volume. For details on creating shapes that satisfy this requirement, see SCNPhysicsShape.

`from`  

A transform matrix representing the initial position and orientation of the shape.

`to`  

A transform matrix representing the final position and orientation of the shape.

`options`  

A dictionary of options affecting the test, or `nil` to use default options. For applicable keys and the possible values, see `Physics Test Options Keys`.

## Return Value

An array of SCNPhysicsContact objects describing any contacts that would occur when moving the physics shape through the physics world.

## Discussion

Use this method when it’s important to plan for (or avoid) collisions ahead of the physics simulation. For example, in a game you might plan maneuvers for a flying character to fit through the gaps between static bodies in the physics world, as illustrated below:

```
// Look for potential collisions along the spaceship's current path.
SCNMatrix4 current = spaceship.transform;
SCNMatrix4 upAhead = SCNMatrix4Translate(current, 0, 0, LOOK_AHEAD_DISTANCE);
NSArray *contacts = [physicsWorld convexSweepTestWithShape:spaceship.physicsBody.physicsShape
                                             fromTransform:current
                                               toTransform:upAhead
                                                   options:nil];
if (contacts.count == 0) {
    // Flight path looks okay.
} else {
    // Flight path will cause a collision: look for another way around.
}
```

## See Also

### Searching for Physics Bodies

func rayTestWithSegment(from: SCNVector3, to: SCNVector3, options: [SCNPhysicsWorld.TestOption : Any]?) -> [SCNHitTestResult]

Searches for physics bodies along a line segment between two points in the physics world.

