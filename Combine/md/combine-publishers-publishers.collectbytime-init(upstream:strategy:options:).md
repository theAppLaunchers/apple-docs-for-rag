

- Combine
- Publishers
- Publishers.CollectByTime
-  init(upstream:strategy:options:) 

Initializer

# init(upstream:strategy:options:)

Creates a publisher that buffers and periodically publishes its items.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
init(
    upstream: Upstream,
    strategy: Publishers.TimeGroupingStrategy,
    options: Context.SchedulerOptions?
)
```

## Parameters 

`upstream`  

The publisher that this publisher receives elements from.

`strategy`  

The strategy with which to collect and publish elements.

`options`  

`Scheduler` options to use for the strategy.

