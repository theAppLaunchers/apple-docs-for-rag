

- UIKit
- UIPercentDrivenInteractiveTransition
-  update(\_:) 

Instance Method

# update(\_:)

Updates the completion percentage of the transition.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
func update(_ percentComplete: CGFloat)
```

## Parameters 

`percentComplete`  

The percentage of the transition that is currently complete, specified as a floating-point number in the range `0.0` to `1.0`. If you specify a value less than `0.0`, this method changes it to `0.0`. Specifying a value greater than `1.0` would cause the animation to appear complete already.

## Discussion

This is a convenience method that calls through to the updateInteractiveTransition(_:) method of the context object.

While tracking user events, your code should call this method regularly to update the current progress toward completing the transition. If, during tracking, the interactions cross a threshold that you consider signifies the completion or cancellation of the transition, stop tracking events and call the finish() or cancel() method.

## See Also

### Managing a transition

func pause()

Pauses an interruptible transition animation.

func cancel()

Notifies the system that user interactions canceled the transition.

func finish()

Notifies the system that user interactions signaled the completion of the transition.

