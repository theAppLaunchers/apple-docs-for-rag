

- UIKit
- UIViewPropertyAnimator
-  addAnimations(\_:delayFactor:) 

Instance Method

# addAnimations(\_:delayFactor:)

Adds the specified animation block with a delay.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+tvOS 10.0+visionOS 1.0+

``` source
@MainActor
func addAnimations(
    _ animation: @escaping () -> Void,
    delayFactor: CGFloat
)
```

## Parameters 

`animation`  

A block containing the animations you want to add to the animator object. This block has no return value and takes no parameters. This parameter must not be `nil`.

`delayFactor`  

The factor to use for delaying the start of the animations. The value you specify must be between `0.0` and `1.0`. This value is multiplied by the animator’s remaining duration to determine the actual delay in seconds. For example, specifying the value `0.5` when the duration is `2.0` results in a one second delay for the start of the animations.

## Discussion

Use this method to add new animation blocks to the animator. The animations in the new block run alongside any previously configured animations after the specified delay. Blocks added while the animator’s state is UIViewAnimatingState.inactive are executed over the time specified by the duration property minus any delay. Blocks added while the animator’s state is UIViewAnimatingState.active are executed over the remaining portion of the total run time minus the delay. For example, if the duration is `2.0` and you add an animation block with a delay factor of `0.25` to a running animator whose fractionComplete property is `0.25`, the animations run for `1.0` second.

If the `animation` block modifies a property that is being modified by a different property animator, then the animators combine their changes in the most appropriate way. For many properties, the changes from each animator are added together to yield a new intermediate value. If a property cannot be modified in this additive manner, the new animations take over as if the beginFromCurrentState option had been specified for a view-based animation.

You can call this method multiple times to add multiple blocks to the animator. It is a programmer error to call this method when the animator’s state property is set to UIViewAnimatingState.stopped.

## See Also

### Modifying animations

func addAnimations(() -> Void)

Adds the specified animation block to the animator.

func addCompletion((UIViewAnimatingPosition) -> Void)

Adds the specified completion block to the animator.

func continueAnimation(withTimingParameters: (any UITimingCurveProvider)?, durationFactor: CGFloat)

Adjusts the timing and duration of a paused animation.

