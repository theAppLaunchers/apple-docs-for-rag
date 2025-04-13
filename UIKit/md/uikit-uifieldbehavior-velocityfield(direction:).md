

- UIKit
- UIFieldBehavior
-  velocityField(direction:) 

Type Method

# velocityField(direction:)

Creates and returns a field behavior object that applies a directional velocity to items.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+tvOS 9.0+visionOS 1.0+

``` source
@MainActor
class func velocityField(direction: CGVector) -> Self
```

## Parameters 

`direction`  

The vector indicating the direction of the velocity force. You can change this value later by modifying the direction property.

## Return Value

A field behavior object that applies a velocity to items.

## Discussion

Velocity fields apply their velocity to the item, overriding any other acceleration forces currently on the item. The vector in the `direction` parameter is combined with the field strength to determine the velocity of items in the field.

## See Also

### Getting the field behaviors

class func dragField() -> Self

Creates and returns a field behavior for slowing an object’s velocity.

class func springField() -> Self

Creates and returns a spring field behavior.

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

