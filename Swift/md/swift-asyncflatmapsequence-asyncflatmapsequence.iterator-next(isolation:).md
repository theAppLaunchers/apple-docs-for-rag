

- Swift
- AsyncFlatMapSequence
- AsyncFlatMapSequence.Iterator
-  next(isolation:) 

Instance Method

# next(isolation:)

Produces the next element in the flat map sequence.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
mutating func next(isolation actor: isolated (any Actor)?) async throws(AsyncFlatMapSequence.Failure) -> SegmentOfResult.Element?
```

## Discussion

This iterator calls `next(isolation:)` on its base iterator; if this call returns `nil`, `next(isolation:)` returns `nil`. Otherwise, `next(isolation:)` calls the transforming closure on the received element, takes the resulting asynchronous sequence, and creates an asynchronous iterator from it. `next(isolation:)` then consumes values from this iterator until it terminates. At this point, `next(isolation:)` is ready to receive the next value from the base sequence.

