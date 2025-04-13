

- AppKit
- NSAnimationDelegate
-  animation(\_:didReachProgressMark:) 

Instance Method

# animation(\_:didReachProgressMark:)

Sent to the delegate when an animation reaches a specific progress mark.

macOS

``` source
nonisolated
optional func animation(
    _ animation: NSAnimation,
    didReachProgressMark progress: NSAnimation.Progress
)
```

## Parameters 

`animation`  

A running `NSAnimation` object that has reached a progress mark.

`progress`  

A `float` value (typed as `NSAnimationProgress`) that indicates a progress mark of `animation`.

## Discussion

The delegate typically implements this method to perform some animation effect for the time slice indicated by `progress`, such as redrawing objects in a view with new coordinates or changing the frame location or size of a window or view. As an alternative to this delegation message, you may choose to observe the progressMarkNotification notification.

