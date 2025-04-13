

- UIKit
-  UIPushBehavior 

Class

# UIPushBehavior

A behavior that applies a continuous or instantaneous force to one or more dynamic items, causing those items to change position accordingly.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
class UIPushBehavior
```

## Overview

A *dynamic item* is any iOS or custom object that conforms to the UIDynamicItem protocol. The UIView and UICollectionViewLayoutAttributes classes implement this protocol starting in iOS 7.0. You can use a custom object as a dynamic item for such purposes as reacting to rotation or position changes computed by a dynamic animator—an instance of the UIDynamicAnimator class.

The default magnitude of a push behavior’s force vector is `nil`, equivalent to no force. A continuous force vector with a magnitude of `1.0`, applied to a 100 point x 100 point view whose density value is `1.0`, results in view acceleration of 100 points / second² in the direction of the vector; this value is also known as the UIKit Newton.

You express a push behavior’s force vector in terms of magnitude (magnitude) and radian angle (angle). Instead of using radian angle, you can equivalently express direction using *x* and *y* components by using the pushDirection property. Whichever approach you use, the alternate, equivalent values update automatically.

For each dynamic item that you associate with a push, the force is applied at the item center or at a specified offset from the center in item-relative coordinates.

To use a push behavior with a dynamic item, perform these two steps:

1.  Associate the item with the behavior using the addItem(_:) method, or initialize a new push behavior with an array of items using the init(items:mode:) method

2.  Enable the behavior by adding it to an animator using the addBehavior(_:) method

After enabling a push behavior, you can activate it and deactivate it using the active property.

The coordinate system that pertains to a push behavior, and the types of dynamic items you can use with the behavior, depend on how you initialized the associated animator. For details, read the Overview of UIDynamicAnimator.

You can include a push behavior in a custom, composite behavior by starting with a UIDynamicBehavior object and adding a push behavior with the addChildBehavior(_:) method. If you want to influence a push behavior at each step of a dynamic animation, implement the inherited action method.

## Topics

### Initializing and managing a push behavior

var active: Bool

The state of the push behavior’s force: either active or inactive.

func addItem(any UIDynamicItem)

Adds a dynamic item to the behavior’s dynamic item array.

init(items: [any UIDynamicItem], mode: UIPushBehavior.Mode)

Initializes a push behavior with an array of dynamic items.

func removeItem(any UIDynamicItem)

Removes a specific dynamic item from the behavior.

var items: [any UIDynamicItem]

Returns the set of dynamic items you’ve added to the push behavior.

### Configuring a push behavior

func setAngle(CGFloat, magnitude: CGFloat)

Sets the angle and magnitude of the force vector for the behavior.

var angle: CGFloat

The angle, in radians, of the force vector for the behavior.

var magnitude: CGFloat

The magnitude of the force vector for the push behavior.

var mode: UIPushBehavior.Mode

Returns the force mode for the push behavior.

func setTargetOffsetFromCenter(UIOffset, for: any UIDynamicItem)

Sets the offset, from the center of a dynamic item, at which to apply the push behavior’s force vector.

func targetOffsetFromCenter(for: any UIDynamicItem) -> UIOffset

Returns the offset, from the center of a dynamic item, at which the push behavior’s force vector is applied.

var pushDirection: CGVector

The direction of the force vector for the behavior, expressed as *x* and *y* components and using standard UIKit geometry.

### Constants

enum Mode

The type of force for the push behavior.

## Relationships

### Inherits From

- UIDynamicBehavior

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol
- Sendable

## See Also

### Behaviors

class UIDynamicBehavior

An object that confers a behavioral configuration on one or more dynamic items, for their participation in 2D animation.

class UIAttachmentBehavior

A relationship between two dynamic items, or between a dynamic item and an anchor point.

class UICollisionBehavior

An object that confers to a specified array of dynamic items the ability to engage in collisions with each other and with the behavior’s specified boundaries.

class UIFieldBehavior

An object that applies field-based physics to dynamic items.

class UIGravityBehavior

An object that applies a gravity-like force to all of its associated dynamic items.

class UISnapBehavior

A spring-like behavior whose initial motion is damped over time so that the object settles at a specific point.

