

- UIKit
- UIView
-  transition(from:to:duration:options:completion:) 

Type Method

# transition(from:to:duration:options:completion:)

Creates a transition animation between the specified views using the given parameters.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
class func transition(
    from fromView: UIView,
    to toView: UIView,
    duration: TimeInterval,
    options: UIView.AnimationOptions = [],
    completion: ((Bool) -> Void)? = nil
)
```

## Parameters 

`fromView`  

The starting view for the transition. By default, this view is removed from its superview as part of the transition.

`toView`  

The ending view for the transition. By default, this view is added to the superview of `fromView` as part of the transition.

`duration`  

The duration of the transition animation, measured in seconds. If you specify a negative value or `0`, the transition is made without animations.

`options`  

A mask of options indicating how you want to perform the animations. For a list of valid constants, see UIView.AnimationOptions.

`completion`  

A block object to be executed when the animation sequence ends. This block has no return value and takes a single Boolean argument that indicates whether or not the animations actually finished before the completion handler was called. If the duration of the animation is 0, this block is performed at the beginning of the next run loop cycle. This parameter may be `NULL`.

## Discussion

This method provides a simple way to transition from the view in the `fromView` parameter to the view in the `toView` parameter. By default, the view in `fromView` is replaced in the view hierarchy by the view in `toView`. If both views are already part of your view hierarchy, you can include the showHideTransitionViews option in the `options` parameter to simply hide or show them.

This method modifies the views in their view hierarchy only. It does not modify your application’s view controllers in any way. For example, if you use this method to change the root view displayed by a view controller, it is your responsibility to update the view controller appropriately to handle the change.

The view transition starts immediately unless another animation is already in-flight, in which case it starts immediately after the current animation finishes.

During an animation, user interactions are temporarily disabled for the views being animated. (Prior to iOS 5, user interactions are disabled for the entire application.) If you want users to be able to interact with the views, include the allowUserInteraction constant in the `options` parameter.

## See Also

### Animating views

static func animate(with: Animation, changes: () -> Void, completion: (() -> Void)?)

Animates changes to one or more views using the specified SwiftUI animation.

class func animate(springDuration: TimeInterval, bounce: CGFloat, initialSpringVelocity: CGFloat, delay: TimeInterval, options: UIView.AnimationOptions, animations: () -> Void, completion: ((Bool) -> Void)?)

Animates changes to one or more views using a spring animation with the specified duration, bounce, initial velocity, delay, options, and completion handler.

class func animate(withDuration: TimeInterval, delay: TimeInterval, options: UIView.AnimationOptions, animations: () -> Void, completion: ((Bool) -> Void)?)

Animate changes to one or more views using the specified duration, delay, options, and completion handler.

class func animate(withDuration: TimeInterval, animations: () -> Void, completion: ((Bool) -> Void)?)

Animate changes to one or more views using the specified duration and completion handler.

class func animate(withDuration: TimeInterval, animations: () -> Void)

Animate changes to one or more views using the specified duration.

class func transition(with: UIView, duration: TimeInterval, options: UIView.AnimationOptions, animations: (() -> Void)?, completion: ((Bool) -> Void)?)

Creates a transition animation for the specified container view.

class func animateKeyframes(withDuration: TimeInterval, delay: TimeInterval, options: UIView.KeyframeAnimationOptions, animations: () -> Void, completion: ((Bool) -> Void)?)

Creates an animation block object that can be used to set up keyframe-based animations for the current view.

class func addKeyframe(withRelativeStartTime: Double, relativeDuration: Double, animations: () -> Void)

Specifies the timing and animation values for a single frame of a keyframe animation.

class func perform(UIView.SystemAnimation, on: [UIView], options: UIView.AnimationOptions, animations: (() -> Void)?, completion: ((Bool) -> Void)?)

Performs a specified system-provided animation on one or more views, along with optional parallel animations that you define.

class func animate(withDuration: TimeInterval, delay: TimeInterval, usingSpringWithDamping: CGFloat, initialSpringVelocity: CGFloat, options: UIView.AnimationOptions, animations: () -> Void, completion: ((Bool) -> Void)?)

Performs a view animation using a timing curve corresponding to the motion of a physical spring.

class func performWithoutAnimation(() -> Void)

Disables a view transition animation.

class func modifyAnimations(withRepeatCount: CGFloat, autoreverses: Bool, animations: () -> Void)

Repeats the specified animations a specific number of times, optionally running the animation forward and backward.

