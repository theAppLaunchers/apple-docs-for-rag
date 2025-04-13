

- Swift
- RangeSet
- RangeSet.Ranges
-  enumerated() 

Instance Method

# enumerated()

Returns a sequence of pairs (*n*, *x*), where *n* represents a consecutive integer starting at zero and *x* represents an element of the sequence.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func enumerated() -> EnumeratedSequence
```

## Return Value

A sequence of pairs enumerating the sequence.

## Discussion

This example enumerates the characters of the string “Swift” and prints each character along with its place in the string.

```
for (n, c) in "Swift".enumerated() {
    print("\(n): '\(c)'")
}
// Prints "0: 'S'"
// Prints "1: 'w'"
// Prints "2: 'i'"
// Prints "3: 'f'"
// Prints "4: 't'"
```

When you enumerate a collection, the integer part of each pair is a counter for the enumeration, but is not necessarily the index of the paired value. These counters can be used as indices only in instances of zero-based, integer-indexed collections, such as `Array` and `ContiguousArray`. For other collections the counters may be out of range or of the wrong type to use as an index. To iterate over the elements of a collection with its indices, use the `zip(_:_:)` function.

This example iterates over the indices and elements of a set, building a list consisting of indices of names with five or fewer letters.

```
let names: Set = ["Sofia", "Camilla", "Martina", "Mateo", "Nicolás"]
var shorterIndices: [Set.Index] = []
for (i, name) in zip(names.indices, names) {
    if name.count 

Now that the `shorterIndices` array holds the indices of the shorter names in the `names` set, you can use those indices to access elements in the set.

```
for i in shorterIndices {
    print(names[i])
}
// Prints "Sofia"
// Prints "Mateo"
```

Complexity

O(1)

