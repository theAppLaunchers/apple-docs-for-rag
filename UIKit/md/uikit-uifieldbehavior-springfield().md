

- UIKit
- UIFieldBehavior
-  springField() 

Type Method

# springField()

Creates and returns a spring field behavior.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+tvOS 9.0+visionOS 1.0+

``` source
@MainActor
class func springField() -> Self
```

## Return Value

A field behavior object that applies spring effects to items.

## Discussion

A spring field behavior object uses Hooke’s law to calculate the force applied to objects in the field. With this law, the amount of force is linearly proportional to the distance from the center of the field. An item entering this field oscillates with a period proportional to the inverse of its density. You can use this field behavior to keep items confined to a particular region. Use the item’s resistance to reduce its linear velocity (and thus the amount of oscillation) over time.

An item in a spring field oscillates continuously unless the spring forces are damped by friction or the item is affected by other fields.

## See Also

### Getting the field behaviors

class func dragField() -> Self

Creates and returns a field behavior for slowing an object’s velocity.

class func velocityField(direction: CGVector) -> Self

Creates and returns a field behavior object that applies a directional velocity to items.

class func electricField() -> Self

Creates and returns a field behavior object that interacts with charged items.

class func magneticField() -> Self

Creates and returns a field behavior that interacts with charged items.

class func radialGravityField(position: CGPoint) -> Self

Creates and returns a field behavior object that models a radial gravitational force.

class func linearGravityField(direction: CGVector) -> Self

Creates and returns a field behavior object that models a linear gravitational force.

class func vortexField() -> Self

Creates and returns a field behavior object that applies a rotational force relative to the field’s position.

class func noiseField(smoothness: CGFloat, animationSpeed: CGFloat) -> Self

Creates and returns a field behavior object that applies random noise to other forces.

class func turbulenceField(smoothness: CGFloat, animationSpeed: CGFloat) -> Self

Creates and returns a field behavior object that applies noise to an item in motion.

class func field(evaluationBlock: (UIFieldBehavior, CGPoint, CGVector, CGFloat, CGFloat, TimeInterval) -> CGVector) -> Self

Creates and returns a field behavior object that applies an app-specified field to items.

