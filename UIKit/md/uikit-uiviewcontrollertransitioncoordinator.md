

- UIKit
-  UIViewControllerTransitionCoordinator 

Protocol

# UIViewControllerTransitionCoordinator

A set of methods that provides support for animations associated with a view controller transition.

iOSiPadOSMac CatalysttvOSvisionOS

``` source
@MainActor
protocol UIViewControllerTransitionCoordinator : UIViewControllerTransitionCoordinatorContext
```

## Overview

Typically, you don’t adopt this protocol in your own classes. When you present or dismiss a view controller, UIKit creates a transition coordinator object automatically and assigns it to the view controller’s transitionCoordinator property. That transition coordinator object is ephemeral and lasts for the duration of the transition animation.

You can use a transition coordinator object to perform tasks that are related to a transition but that are separate from what the animator objects are doing. During a transition, the animator objects are responsible for putting the new view controller content onscreen, but there may be other visual elements that need to be displayed too. For example, a presentation controller might want to animate the appearance or disappearance of decoration views that are separate from the view controller content. In that case, it uses the transition coordinator to perform those animations.

The transition coordinator works with the animator objects to ensure that any extra animations are performed in the same animation group as the transition animations. Having the animations in the same group means that they execute at the same time and can all respond to timing changes provided by an interactive animator object. These timing adjustments happen automatically and don’t require any extra code on your part.

Using the transition coordinator to handle view hierarchy animations is preferred over making those same changes in the viewWillAppear(_:) or similar methods of your view controllers. The blocks you register with the methods of this protocol are guaranteed to execute at the same time as the transition animations. More importantly, the transition coordinator provides important information about the state of the transition, such as whether it was canceled, to your animation blocks through the UIViewControllerTransitionCoordinatorContext object.

In addition to registering animations to perform during the transition, you can call the notifyWhenInteractionEnds(_:) method to register a block to clean up animations associated with an interactive transition. Cleaning up is particularly important when the user cancels a transition interactively. When a cancellation occurs, you need to return to the original view hierarchy state as it existed before the transition.

Because the transition coordinator is in effect only during a transition, UIKit releases the object when the transition finishes and the final callback is made.

## Topics

### Responding to view controller transition progress

func animate(alongsideTransition: ((any UIViewControllerTransitionCoordinatorContext) -> Void)?, completion: ((any UIViewControllerTransitionCoordinatorContext) -> Void)?) -> Bool

Runs the specified animations at the same time as the view controller transition animations.

**Required**

func animateAlongsideTransition(in: UIView?, animation: ((any UIViewControllerTransitionCoordinatorContext) -> Void)?, completion: ((any UIViewControllerTransitionCoordinatorContext) -> Void)?) -> Bool

Runs the specified animations in a view that’s outside of the designated container view.

**Required**

func notifyWhenInteractionChanges((any UIViewControllerTransitionCoordinatorContext) -> Void)

Registers a block to be executed when a transition changes from interactive to non-interactive.

**Required**

func notifyWhenInteractionEnds((any UIViewControllerTransitionCoordinatorContext) -> Void)

Registers a block to be executed when a transition changes from interactive to non-interactive.

**Required**

Deprecated

## Relationships

### Inherits From

- NSObjectProtocol
- UIViewControllerTransitionCoordinatorContext

## See Also

### Transition coordinators

protocol UIViewControllerTransitionCoordinatorContext

A set of methods that provides information about an in-progress view controller transition.

