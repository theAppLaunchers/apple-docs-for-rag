

- Swift
- AsyncFlatMapSequence
-  map(\_:) 

Instance Method

# map(\_:)

Creates an asynchronous sequence that maps the given closure over the asynchronous sequence’s elements.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
@preconcurrency
func map(_ transform: @escaping (Self.Element) async -> Transformed) -> AsyncMapSequence
```

## Parameters 

`transform`  

A mapping closure. `transform` accepts an element of this sequence as its parameter and returns a transformed value of the same or of a different type.

## Return Value

An asynchronous sequence that contains, in order, the elements produced by the `transform` closure.

## Discussion

Use the `map(_:)` method to transform every element received from a base asynchronous sequence. Typically, you use this to transform from one type of element to another.

In this example, an asynchronous sequence called `Counter` produces `Int` values from `1` to `5`. The closure provided to the `map(_:)` method takes each `Int` and looks up a corresponding `String` from a `romanNumeralDict` dictionary. This means the outer `for await in` loop iterates over `String` instances instead of the underlying `Int` values that `Counter` produces:

```
let romanNumeralDict: [Int: String] =
    [1: "I", 2: "II", 3: "III", 5: "V"]

let stream = Counter(howHigh: 5)
    .map { romanNumeralDict[$0] ?? "(unknown)" }
for await numeral in stream {
    print(numeral, terminator: " ")
}
// Prints "I II III (unknown) V "
```

