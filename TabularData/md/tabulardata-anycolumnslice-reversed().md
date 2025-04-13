

- TabularData
- AnyColumnSlice
-  reversed() 

Instance Method

# reversed()

Returns a view presenting the elements of the collection in reverse order.

TabularDataSwiftiOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
func reversed() -> ReversedCollection
```

## Discussion

You can reverse a collection without allocating new space for its elements by calling this `reversed()` method. A `ReversedCollection` instance wraps an underlying collection and provides access to its elements in reverse order. This example prints the characters of a string in reverse order:

```
let word = "Backwards"
for char in word.reversed() {
    print(char, terminator: "")
}
// Prints "sdrawkcaB"
```

If you need a reversed collection of the same type, you may be able to use the collection’s sequence-based or collection-based initializer. For example, to get the reversed version of a string, reverse its characters and initialize a new `String` instance from the result.

```
let reversedWord = String(word.reversed())
print(reversedWord)
// Prints "sdrawkcaB"
```

Complexity

O(1)

## See Also

### Creating a Derivative Column Slice

var lazy: LazySequence&lt;Self>

A sequence containing the same elements as this sequence, but on which some operations, such as `map` and `filter`, are implemented lazily.

