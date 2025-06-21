*   [UIKit](/documentation/uikit)
*   [UIView](/documentation/uikit/uiview)
*   animate(springDuration:bounce:initialSpringVelocity:delay:options:animations:completion:)

Type Method

# animate(springDuration:bounce:initialSpringVelocity:delay:options:animations:completion:)

Animates changes to one or more views using a spring animation with the specified duration, bounce, initial velocity, delay, options, and completion handler.

iOS 17.0+iPadOS 17.0+Mac CatalystmacOS 14.0+tvOS 17.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
@[`MainActor`](/documentation/Swift/MainActor) @preconcurrency
class func animate(
    springDuration duration: [`TimeInterval`](/documentation/Foundation/TimeInterval) = 0.5,
    bounce: [`CGFloat`](/documentation/CoreFoundation/CGFloat-swift.struct) = 0.0,
    initialSpringVelocity: [`CGFloat`](/documentation/CoreFoundation/CGFloat-swift.struct) = 0.0,
    delay: [`TimeInterval`](/documentation/Foundation/TimeInterval) = 0.0,
    options: [`UIView`](/documentation/uikit/uiview).[`AnimationOptions`](/documentation/uikit/uiview/animationoptions) = [],
    animations: () -> [`Void`](/documentation/Swift/Void),
    completion: (([`Bool`](/documentation/Swift/Bool)) -> [`Void`](/documentation/Swift/Void))? = nil
)
```

```
```
```
```
```
```
```

## [Discussion](/documentation/UIKit/UIView/animate\(springDuration:bounce:initialSpringVelocity:delay:options:animations:completion:\)#Discussion)

Related sessions from WWDC23

Session 10055: [What’s new in UIKit](https://developer.apple.com/videos/play/wwdc2023/10055/)

## [See Also](/documentation/UIKit/UIView/animate\(springDuration:bounce:initialSpringVelocity:delay:options:animations:completion:\)#see-also)

### [Animating views](/documentation/UIKit/UIView/animate\(springDuration:bounce:initialSpringVelocity:delay:options:animations:completion:\)#Animating-views)

```swift
```swift
```swift
```swift
class func animate(withDuration: TimeInterval, delay: TimeInterval, options: UIView.AnimationOptions, animations: () -> Void, completion: ((Bool) -> Void)?)
```
```

Animate changes to one or more views using the specified duration, delay, options, and completion handler.
```
```swift
```swift
```swift
class func animate(withDuration: TimeInterval, animations: () -> Void, completion: ((Bool) -> Void)?)
```
```

Animate changes to one or more views using the specified duration and completion handler.
```
```swift
```swift
```swift
class func animate(withDuration: TimeInterval, animations: () -> Void)
```
```

Animate changes to one or more views using the specified duration.
```
```swift
```swift
```swift
class func transition(with: UIView, duration: TimeInterval, options: UIView.AnimationOptions, animations: (() -> Void)?, completion: ((Bool) -> Void)?)
```
```

Creates a transition animation for the specified container view.
```
```swift
```swift
```swift
class func transition(from: UIView, to: UIView, duration: TimeInterval, options: UIView.AnimationOptions, completion: ((Bool) -> Void)?)
```
```

Creates a transition animation between the specified views using the given parameters.
```
```swift
```swift
```swift
class func animateKeyframes(withDuration: TimeInterval, delay: TimeInterval, options: UIView.KeyframeAnimationOptions, animations: () -> Void, completion: ((Bool) -> Void)?)
```
```

Creates an animation block object that can be used to set up keyframe-based animations for the current view.
```
```swift
```swift
```swift
class func addKeyframe(withRelativeStartTime: Double, relativeDuration: Double, animations: () -> Void)
```
```

Specifies the timing and animation values for a single frame of a keyframe animation.
```
```swift
```swift
```swift
class func perform(UIView.SystemAnimation, on: [UIView], options: UIView.AnimationOptions, animations: (() -> Void)?, completion: ((Bool) -> Void)?)
```
```

Performs a specified system-provided animation on one or more views, along with optional parallel animations that you define.
```
```swift
```swift
```swift
class func animate(withDuration: TimeInterval, delay: TimeInterval, usingSpringWithDamping: CGFloat, initialSpringVelocity: CGFloat, options: UIView.AnimationOptions, animations: () -> Void, completion: ((Bool) -> Void)?)
```
```

Performs a view animation using a timing curve corresponding to the motion of a physical spring.
```
```swift
```swift
```swift
class func performWithoutAnimation(() -> Void)
```
```

Disables a view transition animation.
```
```swift
```swift
```swift
class func modifyAnimations(withRepeatCount: CGFloat, autoreverses: Bool, animations: () -> Void)
```
```

Repeats the specified animations a specific number of times, optionally running the animation forward and backward.
```
```