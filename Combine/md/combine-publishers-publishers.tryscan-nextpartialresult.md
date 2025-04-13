

- Combine
- Publishers
- Publishers.TryScan
-  nextPartialResult 

Instance Property

# nextPartialResult

An error-throwing closure that takes as its arguments the previous value returned by the closure and the next element emitted from the upstream publisher.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
let nextPartialResult: (Output, Upstream.Output) throws -> Output
```

## See Also

### Inspecting Publisher Properties

let upstream: Upstream

The publisher that this publisher receives elements from.

let initialResult: Output

The previous result returned by the `nextPartialResult` closure.

