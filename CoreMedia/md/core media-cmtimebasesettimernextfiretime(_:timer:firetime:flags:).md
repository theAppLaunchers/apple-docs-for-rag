

- Core Media
-  CMTimebaseSetTimerNextFireTime(\_:timer:fireTime:flags:) 

Function

# CMTimebaseSetTimerNextFireTime(\_:timer:fireTime:flags:)

Sets the time on the timebase’s timeline at which the timer should fire next.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+macOS 10.8+tvOS 9.0+visionOS 1.0+watchOS 6.0+

``` source
func CMTimebaseSetTimerNextFireTime(
    _ timebase: CMTimebase,
    timer: CFRunLoopTimer,
    fireTime: CMTime,
    flags: UInt32
) -> OSStatus
```

## Discussion

The timer must be on the list of timers the timebase manages. The timebase continues to update the timer’s “NextFireDate” according to time jumps and effective rate changes. If `fireTime` is not numeric, or if the timebase is not moving, the “NextFireDate” is set to a future date.

Due to the way that `CFRunLoopTimers` are implemented, if a timer passes through a state in which it is due to fire, it may fire even if its rescheduled before the runloop runs again. Clients should take care to avoid temporarily scheduling timers in the past. For example, set the timebase’s rate or time before you set the timer’s next fire time, if you are doing both at once. If setting the timebase’s rate or time might put the timer’s fire time in the past, you may need to set the fire time to `kCMTimeInvalid` across the timebase change.

## See Also

### Interacting with Timers

func CMTimebaseAddTimer(CMTimebase, timer: CFRunLoopTimer, runloop: CFRunLoop) -> OSStatus

Adds the timer to the list of timers the timebase manages.

func CMTimebaseAddTimerDispatchSource(CMTimebase, timerSource: dispatch_source_t) -> OSStatus

Adds the timer dispatch source to the list of timers the timebase manages.

func CMTimebaseRemoveTimer(CMTimebase, timer: CFRunLoopTimer) -> OSStatus

Removes the timer from the list of timers the timebase manages.

func CMTimebaseRemoveTimerDispatchSource(CMTimebase, timerSource: dispatch_source_t) -> OSStatus

Removes the timer dispatch source from the list of timers the timebase manages.

func CMTimebaseSetTimerToFireImmediately(CMTimebase, timer: CFRunLoopTimer) -> OSStatus

Sets the timer to fire immediately once, overriding any previous timer calls.

func CMTimebaseSetTimerDispatchSourceNextFireTime(CMTimebase, timerSource: dispatch_source_t, fireTime: CMTime, flags: UInt32) -> OSStatus

Sets the time on the timebase’s timeline at which the timer dispatch source should fire next.

func CMTimebaseSetTimerDispatchSourceToFireImmediately(CMTimebase, timerSource: dispatch_source_t) -> OSStatus

Sets the timer dispatch source to fire immediately once, overriding any previous timer call.

