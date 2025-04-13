

- UIKit
- UIFieldBehavior
-  electricField() 

Type Method

# electricField()

Creates and returns a field behavior object that interacts with charged items.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+tvOS 9.0+visionOS 1.0+

``` source
@MainActor
class func electricField() -> Self
```

## Return Value

An field behavior object that applies an electric field to charged items.

## Discussion

The amount of force applied by the field is proportional to the charge of the item and is modeled after the first part of the Lorentz equation (`F = qE`). This equation means that the force equals the charge of the object multiplied by the strength of the electric field at the item’s current location in that field.

You can use electric fields as a way to apply forces to an object that are based on charge instead of mass. You can use electric fields to repel or attract items in your interface, with opposite charges attracting each other and similar charges repelling each other. In other words, an item with a positive charge value is attracted to fields whose strength value is negative and repelled by fields whose strength value is positive.

## See Also

### Getting the field behaviors

class func dragField() -> Self

Creates and returns a field behavior for slowing an object’s velocity.

class func springField() -> Self

Creates and returns a spring field behavior.

class func velocityField(direction: CGVector) -> Self

Creates and returns a field behavior object that applies a directional velocity to items.

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

