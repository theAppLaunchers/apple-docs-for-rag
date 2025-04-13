

- Swift
- SuspendingClock
-  sleep(until:tolerance:) 

Instance Method

# sleep(until:tolerance:)

Suspend task execution until a given deadline within a tolerance. If no tolerance is specified then the system may adjust the deadline to coalesce CPU wake-ups to more efficiently process the wake-ups in a more power efficient manner.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
func sleep(
    until deadline: SuspendingClock.Instant,
    tolerance: Duration? = nil
) async throws
```

## Discussion

If the task is canceled before the time ends, this function throws `CancellationError`.

This function doesn’t block the underlying thread.

