

- Combine
- Publishers
- Publishers.TryScan
-  init(upstream:initialResult:nextPartialResult:) 

Initializer

# init(upstream:initialResult:nextPartialResult:)

Creates a publisher that transforms elements from the upstream publisher by providing the current element to a failable closure along with the last value returned by the closure.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
init(
    upstream: Upstream,
    initialResult: Output,
    nextPartialResult: @escaping (Output, Upstream.Output) throws -> Output
)
```

## Parameters 

`upstream`  

The publisher that this publisher receives elements from.

`initialResult`  

The previous result returned by the `nextPartialResult` closure.

`nextPartialResult`  

An error-throwing closure that takes as its arguments the previous value returned by the closure and the next element emitted from the upstream publisher.

