

- Swift
- AsyncThrowingCompactMapSequence
- AsyncThrowingCompactMapSequence.Iterator
-  next(isolation:) 

Instance Method

# next(isolation:)

Produces the next element in the compact map sequence.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
mutating func next(isolation actor: isolated (any Actor)?) async throws -> ElementOfResult?
```

## Discussion

This iterator calls `next()` on its base iterator; if this call returns `nil`, `next()` returns `nil`. Otherwise, `next()` calls the transforming closure on the received element, returning it if the transform returns a non-`nil` value. If the transform returns `nil`, this method continues to wait for further elements until it gets one that transforms to a non-`nil` value. If calling the closure throws an error, the sequence ends and `next()` rethrows the error.

