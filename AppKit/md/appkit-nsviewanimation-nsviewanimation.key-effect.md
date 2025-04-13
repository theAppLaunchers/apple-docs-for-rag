

- AppKit
- NSViewAnimation
- NSViewAnimation.Key
-  effect 

Type Property

# effect

An effect to apply to the animation.

macOS

``` source
static let effect: NSViewAnimation.Key
```

## Discussion

Takes a string constant specifying fade-in or fade-out effects for the target: `NSViewAnimationFadeInEffect` and `NSViewAnimationFadeOutEffect`. If the target is a view and the effect is to fade out, the view is hidden at the end. If the effect is to fade in an initially hidden view and the end frame is non-empty, the view is unhidden at the end. If the target is a window, the window is ordered in or out as appropriate to the effect. This property is optional.

## See Also

### Keys

static let endFrame: NSViewAnimation.Key

The size and location of the window or view at the end of the animation.

static let startFrame: NSViewAnimation.Key

The size and location of the window or view at the start of the animation.

static let target: NSViewAnimation.Key

The target of the animation.

