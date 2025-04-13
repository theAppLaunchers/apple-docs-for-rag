

- Combine
- Publishers
- Publishers.PrefetchStrategy
-  Publishers.PrefetchStrategy.keepFull 

Case

# Publishers.PrefetchStrategy.keepFull

A strategy to fill the buffer at subscription time, and keep it full thereafter.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
case keepFull
```

## Discussion

This strategy starts by making a demand equal to the buffer’s size from the upstream when the subscriber first connects. Afterwards, it continues to demand elements from the upstream to try to keep the buffer full.

## See Also

### Prefetching Strategies

case byRequest

A strategy that avoids prefetching and instead performs requests on demand.

