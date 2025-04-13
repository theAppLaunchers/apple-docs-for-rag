

- Swift
- Dictionary
-  makeIterator() 

Instance Method

# makeIterator()

Returns an iterator over the dictionary’s key-value pairs.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func makeIterator() -> Dictionary.Iterator
```

Available when `Key` conforms to `Hashable`.

## Return Value

An iterator over the dictionary with elements of type `(key: Key, value: Value)`.

## Discussion

Iterating over a dictionary yields the key-value pairs as two-element tuples. You can decompose the tuple in a `for`-`in` loop, which calls `makeIterator()` behind the scenes, or when calling the iterator’s `next()` method directly.

```
let hues = ["Heliotrope": 296, "Coral": 16, "Aquamarine": 156]
for (name, hueValue) in hues {
    print("The hue of \(name) is \(hueValue).")
}
// Prints "The hue of Heliotrope is 296."
// Prints "The hue of Coral is 16."
// Prints "The hue of Aquamarine is 156."
```

## See Also

### Iterating over Keys and Values

func forEach((Self.Element) throws -> Void) rethrows

Calls the given closure on each element in the sequence in the same order as a `for`-`in` loop.

func enumerated() -> EnumeratedSequence&lt;Self>

Returns a sequence of pairs (*n*, *x*), where *n* represents a consecutive integer starting at zero and *x* represents an element of the sequence.

var lazy: LazySequence&lt;Self>

A sequence containing the same elements as this sequence, but on which some operations, such as `map` and `filter`, are implemented lazily.

var underestimatedCount: Int

A value less than or equal to the number of elements in the collection.

