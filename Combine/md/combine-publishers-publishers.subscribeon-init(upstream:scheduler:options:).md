

- Combine
- Publishers
- Publishers.SubscribeOn
-  init(upstream:scheduler:options:) 

Initializer

# init(upstream:scheduler:options:)

Creates a publisher that receives elements from an upstream publisher on a specific scheduler.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
init(
    upstream: Upstream,
    scheduler: Context,
    options: Context.SchedulerOptions?
)
```

## Parameters 

`upstream`  

The publisher from which this publisher receives elements.

`scheduler`  

The scheduler the publisher should use to receive elements.

`options`  

Scheduler options that customize the delivery of elements.

