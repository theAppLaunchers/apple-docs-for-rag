

- Swift
- AsyncThrowingMapSequence
- AsyncThrowingMapSequence.Iterator
-  next() 

Instance Method

# next()

Produces the next element in the map sequence.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
mutating func next() async throws -> Transformed?
```

## Discussion

This iterator calls `next()` on its base iterator; if this call returns `nil`, `next()` returns nil. Otherwise, `next()` returns the result of calling the transforming closure on the received element. If calling the closure throws an error, the sequence ends and `next()` rethrows the error.

