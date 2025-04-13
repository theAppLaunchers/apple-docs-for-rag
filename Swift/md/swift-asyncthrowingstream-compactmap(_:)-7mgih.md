

- Swift
- AsyncThrowingStream
-  compactMap(\_:) 

Instance Method

# compactMap(\_:)

Creates an asynchronous sequence that maps the given closure over the asynchronous sequence’s elements, omitting results that don’t return a value.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
@preconcurrency
func compactMap(_ transform: @escaping (Self.Element) async -> ElementOfResult?) -> AsyncCompactMapSequence
```

## Parameters 

`transform`  

A mapping closure. `transform` accepts an element of this sequence as its parameter and returns a transformed value of the same or of a different type.

## Return Value

An asynchronous sequence that contains, in order, the non-`nil` elements produced by the `transform` closure.

## Discussion

Use the `compactMap(_:)` method to transform every element received from a base asynchronous sequence, while also discarding any `nil` results from the closure. Typically, you use this to transform from one type of element to another.

In this example, an asynchronous sequence called `Counter` produces `Int` values from `1` to `5`. The closure provided to the `compactMap(_:)` method takes each `Int` and looks up a corresponding `String` from a `romanNumeralDict` dictionary. Because there is no key for `4`, the closure returns `nil` in this case, which `compactMap(_:)` omits from the transformed asynchronous sequence.

```
let romanNumeralDict: [Int: String] =
    [1: "I", 2: "II", 3: "III", 5: "V"]

let stream = Counter(howHigh: 5)
    .compactMap { romanNumeralDict[$0] }
for await numeral in stream {
    print(numeral, terminator: " ")
}
// Prints "I II III V "
```

## See Also

### Transforming a Sequence

func map&lt;Transformed>((Self.Element) async -> Transformed) -> AsyncMapSequence&lt;Self, Transformed>

Creates an asynchronous sequence that maps the given closure over the asynchronous sequence’s elements.

func map&lt;Transformed>((Self.Element) async throws -> Transformed) -> AsyncThrowingMapSequence&lt;Self, Transformed>

Creates an asynchronous sequence that maps the given error-throwing closure over the asynchronous sequence’s elements.

func compactMap&lt;ElementOfResult>((Self.Element) async throws -> ElementOfResult?) -> AsyncThrowingCompactMapSequence&lt;Self, ElementOfResult>

Creates an asynchronous sequence that maps an error-throwing closure over the base sequence’s elements, omitting results that don’t return a value.

func flatMap&lt;SegmentOfResult>((Self.Element) async throws -> SegmentOfResult) -> AsyncThrowingFlatMapSequence&lt;Self, SegmentOfResult>

Creates an asynchronous sequence that concatenates the results of calling the given error-throwing transformation with each element of this sequence.

func reduce&lt;Result>(Result, (Result, Self.Element) async throws -> Result) async rethrows -> Result

Returns the result of combining the elements of the asynchronous sequence using the given closure.

func reduce&lt;Result>(into: Result, (inout Result, Self.Element) async throws -> Void) async rethrows -> Result

Returns the result of combining the elements of the asynchronous sequence using the given closure, given a mutable initial value.

