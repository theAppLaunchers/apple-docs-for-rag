

- RealityKit
- ObjectCaptureSession
- ObjectCaptureSession.Updates
-  contains(where:) 

Instance Method

# contains(where:)

Returns a Boolean value that indicates whether the asynchronous sequence contains an element that satisfies the given predicate.

RealityKitSwiftUIiOS 13.0+iPadOS 13.0+macOS 10.15+tvOS 13.0+watchOS 6.0+

``` source
func contains(where predicate: (Self.Element) async throws -> Bool) async rethrows -> Bool
```

## Parameters 

`predicate`  

A closure that takes an element of the asynchronous sequence as its argument and returns a Boolean value that indicates whether the passed element represents a match.

## Return Value

`true` if the sequence contains an element that satisfies predicate; otherwise, `false`.

## Discussion

You can use the predicate to check for an element of a type that doesn’t conform to the `Equatable` protocol, or to find an element that satisfies a general condition.

In this example, an asynchronous sequence called `Counter` produces `Int` values from `1` to `10`. The `contains(where:)` method checks to see whether the sequence produces a value divisible by `3`:

```
let containsDivisibleByThree = await Counter(howHigh: 10)
    .contains { $0 % 3 == 0 }
print(containsDivisibleByThree)
// Prints "true"
```

The predicate executes each time the asynchronous sequence produces an element, until either the predicate finds a match or the sequence ends.

