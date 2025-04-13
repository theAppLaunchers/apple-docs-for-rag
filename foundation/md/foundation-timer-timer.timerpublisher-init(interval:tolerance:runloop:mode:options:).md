

- Foundation
- Timer
- Timer.TimerPublisher
-  init(interval:tolerance:runLoop:mode:options:) 

Initializer

# init(interval:tolerance:runLoop:mode:options:)

Creates a publisher that repeatedly emits the current date on the given interval.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
init(
    interval: TimeInterval,
    tolerance: TimeInterval? = nil,
    runLoop: RunLoop,
    mode: RunLoop.Mode,
    options: RunLoop.SchedulerOptions? = nil
)
```

## Parameters 

`interval`  

The interval on which to publish events.

`tolerance`  

The allowed timing variance when emitting events. Defaults to `nil`, which allows any variance.

`runLoop`  

The run loop on which the timer runs.

`mode`  

The run loop mode in which to run the timer.

`options`  

Scheduler options passed to the timer. Defaults to `nil`.

