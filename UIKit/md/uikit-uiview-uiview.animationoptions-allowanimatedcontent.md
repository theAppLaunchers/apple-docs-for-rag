

- UIKit
- UIView
- UIView.AnimationOptions
-  allowAnimatedContent 

Type Property

# allowAnimatedContent

Animate the views by changing the property values dynamically and redrawing the view.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
static var allowAnimatedContent: UIView.AnimationOptions { get }
```

## Discussion

If this key is not present, the views are animated using a snapshot image.

## See Also

### Constants

static var layoutSubviews: UIView.AnimationOptions

Lay out subviews at commit time so that they are animated along with their parent.

static var allowUserInteraction: UIView.AnimationOptions

Allow the user to interact with views while they are being animated.

static var beginFromCurrentState: UIView.AnimationOptions

Start the animation from the current setting associated with an already in-flight animation.

static var `repeat`: UIView.AnimationOptions

Repeat the animation indefinitely.

static var autoreverse: UIView.AnimationOptions

Run the animation backwards and forwards (must be combined with the repeat option).

static var overrideInheritedDuration: UIView.AnimationOptions

Force the animation to use the original duration value specified when the animation was submitted.

static var overrideInheritedCurve: UIView.AnimationOptions

Force the animation to use the original curve value specified when the animation was submitted.

static var showHideTransitionViews: UIView.AnimationOptions

Hide or show views during a view transition.

static var overrideInheritedOptions: UIView.AnimationOptions

The option to not inherit the animation type or any options.

static var curveEaseInOut: UIView.AnimationOptions

Specify an ease-in ease-out curve, which causes the animation to begin slowly, accelerate through the middle of its duration, and then slow again before completing.

static var curveEaseIn: UIView.AnimationOptions

An ease-in curve causes the animation to begin slowly, and then speed up as it progresses.

static var curveEaseOut: UIView.AnimationOptions

An ease-out curve causes the animation to begin quickly, and then slow as it completes.

static var curveLinear: UIView.AnimationOptions

A linear animation curve causes an animation to occur evenly over its duration.

static var transitionFlipFromLeft: UIView.AnimationOptions

A transition that flips a view around its vertical axis from left to right (the left side of the view moves toward the front and right side toward the back).

static var transitionFlipFromRight: UIView.AnimationOptions

A transition that flips a view around its vertical axis from right to left (the right side of the view moves toward the front and left side toward the back).

