

- Dispatch
- DispatchSourceTimer
-  schedule(wallDeadline:repeating:leeway:) 

Instance Method

# schedule(wallDeadline:repeating:leeway:)

Schedules a timer with the specified time, repeat interval, and leeway values.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOSSwift 4.0+

``` source
func schedule(
    wallDeadline: DispatchWallTime,
    repeating interval: Double,
    leeway: DispatchTimeInterval = .nanoseconds(0)
)
```

## Parameters 

`wallDeadline`  

The time at which to execute the dispatch source’s event handler.

`interval`  

The repeat interval for the timer, measured in seconds.

`leeway`  

The maximum amount of time after `wallDeadline` by which the system may delay the delivery of the timer event.

## Discussion

The system may defer the deliver of timer events to improve power consumption and system performance. The first time the timer fires, the maximum allowable delay is equal to the value in the `leeway` parameter. For subsequent firings of a repeating timer, the timer fires at `wallDeadline + (n * repeating)`, and the maximum delay is equal to `min(leeway, repeating/2)`—that is, the smaller of either the `leeway` value or half the value in the `repeating` parameter.

The system may fire a timer sooner than the value in the `wallDeadline` parameter. If you created the timer with the strict flag, the system makes every effort to observe the provided `leeway` value, even if it is smaller than the current lower limit.

Calling this method on a cancelled dispatch source has no effect.

## See Also

### Scheduling the Timer Trigger Conditions

func schedule(deadline: DispatchTime, repeating: DispatchTimeInterval, leeway: DispatchTimeInterval)

Schedules a timer with the specified deadline, repeat interval, and leeway values.

func schedule(deadline: DispatchTime, repeating: Double, leeway: DispatchTimeInterval)

Schedules a timer with the specified deadline, repeat interval, and leeway values.

func schedule(wallDeadline: DispatchWallTime, repeating: DispatchTimeInterval, leeway: DispatchTimeInterval)

Schedules a timer with the specified time, repeat interval, and leeway values.

