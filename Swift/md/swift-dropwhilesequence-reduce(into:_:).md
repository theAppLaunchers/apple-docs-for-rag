

- Swift
- DropWhileSequence
-  reduce(into:\_:) 

Instance Method

# reduce(into:\_:)

Returns the result of combining the elements of the sequence using the given closure.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func reduce(
    into initialResult: Result,
    _ updateAccumulatingResult: (inout Result, Self.Element) throws -> ()
) rethrows -> Result
```

## Parameters 

`initialResult`  

The value to use as the initial accumulating value.

`updateAccumulatingResult`  

A closure that updates the accumulating value with an element of the sequence.

## Return Value

The final accumulated value. If the sequence has no elements, the result is `initialResult`.

## Discussion

Use the `reduce(into:_:)` method to produce a single value from the elements of an entire sequence. For example, you can use this method on an array of integers to filter adjacent equal entries or count frequencies.

This method is preferred over `reduce(_:_:)` for efficiency when the result is a copy-on-write type, for example an Array or a Dictionary.

The `updateAccumulatingResult` closure is called sequentially with a mutable accumulating value initialized to `initialResult` and each element of the sequence. This example shows how to build a dictionary of letter frequencies of a string.

```
let letters = "abracadabra"
let letterCount = letters.reduce(into: [:]) { counts, letter in
    counts[letter, default: 0] += 1
}
// letterCount == ["a": 5, "b": 2, "r": 2, "c": 1, "d": 1]
```

When `letters.reduce(into:_:)` is called, the following steps occur:

1.  The `updateAccumulatingResult` closure is called with the initial accumulating value—`[:]` in this case—and the first character of `letters`, modifying the accumulating value by setting `1` for the key `"a"`.

2.  The closure is called again repeatedly with the updated accumulating value and each element of the sequence.

3.  When the sequence is exhausted, the accumulating value is returned to the caller.

If the sequence has no elements, `updateAccumulatingResult` is never executed and `initialResult` is the result of the call to `reduce(into:_:)`.

Complexity

O(*n*), where *n* is the length of the sequence.

