

- Objective-C Runtime
- NSObject
-  perform(\_:with:afterDelay:) 

Instance Method

# perform(\_:with:afterDelay:)

Invokes a method of the receiver on the current thread using the default mode after a delay.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
func perform(
    _ aSelector: Selector,
    with anArgument: Any?,
    afterDelay delay: TimeInterval
)
```

## Parameters 

`aSelector`  

A Selector that identifies the method to invoke. The method should not have a significant return value and should take a single argument of type id, or no arguments.

`anArgument`  

The argument to pass to the method when it is invoked. Pass `nil` if the method does not take an argument.

`delay`  

The minimum time before which the message is sent. Specifying a delay of 0 does not necessarily cause the selector to be performed immediately. The selector is still queued on the thread’s run loop and performed as soon as possible.

## Discussion

This method sets up a timer to perform the `aSelector` message on the current thread’s run loop. The timer is configured to run in the default mode (`NSDefaultRunLoopMode`). When the timer fires, the thread attempts to dequeue the message from the run loop and perform the selector. It succeeds if the run loop is running and in the default mode; otherwise, the timer waits until the run loop is in the default mode.

If you want the message to be dequeued when the run loop is in a mode other than the default mode, use the perform(_:with:afterDelay:inModes:) method instead. If you are not sure whether the current thread is the main thread, you can use the performSelector(onMainThread:with:waitUntilDone:) or performSelector(onMainThread:with:waitUntilDone:modes:) method to guarantee that your selector executes on the main thread. To cancel a queued message, use the cancelPreviousPerformRequests(withTarget:) or cancelPreviousPerformRequests(withTarget:selector:object:) method.

### Special Considerations

This method registers with the runloop of its current context, and depends on that runloop being run on a regular basis to perform correctly. One common context where you might call this method and end up registering with a runloop that is not automatically run on a regular basis is when being invoked by a dispatch queue. If you need this type of functionality when running on a dispatch queue, you should use dispatch_after and related methods to get the behavior you want.

## See Also

### Sending Messages

func perform(Selector, with: Any?, afterDelay: TimeInterval, inModes: [RunLoop.Mode])

Invokes a method of the receiver on the current thread using the specified modes after a delay.

func performSelector(onMainThread: Selector, with: Any?, waitUntilDone: Bool)

Invokes a method of the receiver on the main thread using the default mode.

func performSelector(onMainThread: Selector, with: Any?, waitUntilDone: Bool, modes: [String]?)

Invokes a method of the receiver on the main thread using the specified modes.

func perform(Selector, on: Thread, with: Any?, waitUntilDone: Bool)

Invokes a method of the receiver on the specified thread using the default mode.

func perform(Selector, on: Thread, with: Any?, waitUntilDone: Bool, modes: [String]?)

Invokes a method of the receiver on the specified thread using the specified modes.

func performSelector(inBackground: Selector, with: Any?)

Invokes a method of the receiver on a new background thread.

class func cancelPreviousPerformRequests(withTarget: Any)

Cancels perform requests previously registered with the perform(_:with:afterDelay:) instance method.

class func cancelPreviousPerformRequests(withTarget: Any, selector: Selector, object: Any?)

Cancels perform requests previously registered with perform(_:with:afterDelay:).

