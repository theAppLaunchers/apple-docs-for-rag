

- Swift
- AsyncPrefixWhileSequence
-  flatMap(\_:) 

Instance Method

# flatMap(\_:)

Creates an asynchronous sequence that concatenates the results of calling the given transformation with each element of this sequence.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
@preconcurrency
func flatMap(_ transform: @escaping (Self.Element) async -> SegmentOfResult) -> AsyncFlatMapSequence where SegmentOfResult : AsyncSequence, SegmentOfResult.Failure == Never
```

## Parameters 

`transform`  

A mapping closure. `transform` accepts an element of this sequence as its parameter and returns an `AsyncSequence`.

## Return Value

A single, flattened asynchronous sequence that contains all elements in all the asynchronous sequences produced by `transform`.

## Discussion

Use this method to receive a single-level asynchronous sequence when your transformation produces an asynchronous sequence for each element.

In this example, an asynchronous sequence called `Counter` produces `Int` values from `1` to `5`. The transforming closure takes the received `Int` and returns a new `Counter` that counts that high. For example, when the transform receives `3` from the base sequence, it creates a new `Counter` that produces the values `1`, `2`, and `3`. The `flatMap(_:)` method “flattens” the resulting sequence-of-sequences into a single `AsyncSequence`.

```
let stream = Counter(howHigh: 5)
    .flatMap { Counter(howHigh: $0) }
for await number in stream {
    print(number, terminator: " ")
}
// Prints "1 1 2 1 2 3 1 2 3 4 1 2 3 4 5 "
```

