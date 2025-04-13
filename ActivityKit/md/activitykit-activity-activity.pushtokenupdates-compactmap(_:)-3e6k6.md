

- ActivityKit
- Activity
- Activity.PushTokenUpdates
-  compactMap(\_:) 

Instance Method

# compactMap(\_:)

Creates an asynchronous sequence that maps an error-throwing closure over the base sequence’s elements, omitting results that don’t return a value.

ActivityKitSwiftiOS 13.0+iPadOS 13.0+macOS 10.15+tvOS 13.0+watchOS 6.0+

``` source
@preconcurrency
func compactMap(_ transform: @escaping (Self.Element) async throws -> ElementOfResult?) -> AsyncThrowingCompactMapSequence
```

## Parameters 

`transform`  

An error-throwing mapping closure. `transform` accepts an element of this sequence as its parameter and returns a transformed value of the same or of a different type. If `transform` throws an error, the sequence ends.

## Return Value

An asynchronous sequence that contains, in order, the non-`nil` elements produced by the `transform` closure. The sequence ends either when the base sequence ends or when `transform` throws an error.

## Discussion

Use the `compactMap(_:)` method to transform every element received from a base asynchronous sequence, while also discarding any `nil` results from the closure. Typically, you use this to transform from one type of element to another.

In this example, an asynchronous sequence called `Counter` produces `Int` values from `1` to `5`. The closure provided to the `compactMap(_:)` method takes each `Int` and looks up a corresponding `String` from a `romanNumeralDict` dictionary. Since there is no key for `4`, the closure returns `nil` in this case, which `compactMap(_:)` omits from the transformed asynchronous sequence. When the value is `5`, the closure throws `MyError`, terminating the sequence.

```
let romanNumeralDict: [Int: String] =
    [1: "I", 2: "II", 3: "III", 5: "V"]

do {
    let stream = Counter(howHigh: 5)
        .compactMap { (value) throws -> String? in
            if value == 5 {
                throw MyError()
            }
            return romanNumeralDict[value]
        }
    for try await numeral in stream {
        print(numeral, terminator: " ")
    }
} catch {
    print("Error: \(error)")
}
// Prints "I II III Error: MyError() "
```

