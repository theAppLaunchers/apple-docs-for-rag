

- UIKit
- UIView
-  addKeyframe(withRelativeStartTime:relativeDuration:animations:) 

Type Method

# addKeyframe(withRelativeStartTime:relativeDuration:animations:)

Specifies the timing and animation values for a single frame of a keyframe animation.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
class func addKeyframe(
    withRelativeStartTime frameStartTime: Double,
    relativeDuration frameDuration: Double,
    animations: @escaping () -> Void
)
```

## Parameters 

`frameStartTime`  

The time at which to start the specified animations. This value must be in the range `0` to `1`, where `0` represents the start of the overall animation and `1` represents the end of the overall animation. For example, for an animation that is two seconds in duration, specifying a start time of `0.5` causes the animations to begin executing one second after the start of the overall animation.

`frameDuration`  

The length of time over which to animate to the specified value. This value must be in the range `0` to `1` and indicates the amount of time relative to the overall animation length. If you specify a value of `0`, any properties you set in the `animations` block update immediately at the specified start time. If you specify a nonzero value, the properties animate over that amount of time. For example, for an animation that is two seconds in duration, specifying a duration of `0.5` results in an animation duration of one second.

`animations`  

A block object containing the animations you want to perform. This is where you programmatically change any animatable properties of the views in your view hierarchy. This block takes no parameters and has no return value. This parameter must not be `nil`.

## Discussion

To animate view properties during a keyframe animation, call this method from within the animation block you pass to the animateKeyframes(withDuration:delay:options:animations:completion:) method. To animate between different values, or to tweak the timing of your view property animations, you can call this method multiple times within a block.

The view properties you change in the `animations` block animate over the timespan you specify in `frameDuration` parameter. The properties do not begin animating until the time you specify in the `frameStartTime` parameter. After the frame start time, the animation executes over its specified duration or until interrupted by another animation.

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

class func transition(from: UIView, to: UIView, duration: TimeInterval, options: UIView.AnimationOptions, completion: ((Bool) -> Void)?)

Creates a transition animation between the specified views using the given parameters.

class func animateKeyframes(withDuration: TimeInterval, delay: TimeInterval, options: UIView.KeyframeAnimationOptions, animations: () -> Void, completion: ((Bool) -> Void)?)

Creates an animation block object that can be used to set up keyframe-based animations for the current view.

class func perform(UIView.SystemAnimation, on: [UIView], options: UIView.AnimationOptions, animations: (() -> Void)?, completion: ((Bool) -> Void)?)

Performs a specified system-provided animation on one or more views, along with optional parallel animations that you define.

class func animate(withDuration: TimeInterval, delay: TimeInterval, usingSpringWithDamping: CGFloat, initialSpringVelocity: CGFloat, options: UIView.AnimationOptions, animations: () -> Void, completion: ((Bool) -> Void)?)

Performs a view animation using a timing curve corresponding to the motion of a physical spring.

class func performWithoutAnimation(() -> Void)

Disables a view transition animation.

class func modifyAnimations(withRepeatCount: CGFloat, autoreverses: Bool, animations: () -> Void)

Repeats the specified animations a specific number of times, optionally running the animation forward and backward.

