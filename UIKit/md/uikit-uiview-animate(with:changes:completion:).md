

- UIKit
- UIView
-  animate(with:changes:completion:) 

Type Method

# animate(with:changes:completion:)

Animates changes to one or more views using the specified SwiftUI animation.

iOS 18.0–18.0DeprecatediPadOS 18.0–18.0DeprecatedMac CatalysttvOS 18.0–18.0DeprecatedvisionOS 2.0–2.0Deprecated

``` source
@MainActor @preconcurrency
static func animate(
    with animation: Animation = Animation.default,
    changes: () -> Void,
    completion: (() -> Void)? = nil
)
```

## Parameters 

`animation`  

The animation to use for the changes.

`changes`  

A closure that contains the changes to animate.

`completion`  

A closure to execute after the animation completes.

## Discussion

Use this method to leverage SwiftUI animations from UIKit code, creating a more consistent animation experience if your app incorporates code from both frameworks.

Similar to animations in SwiftUI views, you can smoothly retarget the animations you perform using this method, preserving the velocity of the animations. The following code shows a basic example of retargeting an in-progress animation to a different location:

```
import UIKit
import SwiftUI

Task {
    // Begins an animation to move the view to a new location.
    UIView.animate(with: .spring(duration: 1.0)) {
        myView.center = CGPoint(x: 200, y: 200)
    }

    try await Task.sleep(for: .seconds(0.5))

    // Retargets the running animations to move the view to a different location.
    UIView.animate(with: .spring) {
        myView.center = CGPoint(x: 100, y: 400)
    }
}
```

You can also retarget animations continuously. The following code shows an example of retargeting animations during a pan gesture. As a person uses a pan gesture to drag a view across the screen, the pan gesture continuously fires change events. Each change event creates a new animation with the interactiveSpring type, and each new animation retargets the previous one. When the gesture ends, a final noninteractive spring animation uses the velocity from the previous interactiveSpring animations to carry the animation forward with continuous velocity, creating a fluid animation experience.

```
import UIKit
import SwiftUI

switch panGesture.state {
case .changed:
    UIView.animate(with: .interactiveSpring) {
        myView.center = panGesture.translation(in: view)
    }
case .ended:
    UIView.animate(with: .spring) {
        myView.center = .zero
    }
}
```

Note

Animating a UIView using a SwiftUI animation behaves differently from other UIView animations. Unlike other UIView animations, these animations run in-process and don’t have a backing CAAnimation. However, presentation values from these animations still reflect in the presentation layer object (presentation()) of the view’s layer.

For more information, read Unifying your app’s animations.

## See Also

### Animating views

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

