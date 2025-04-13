

- Swift
- AnyRandomAccessCollection
-  popLast() 

Instance Method

# popLast()

Removes and returns the last element of the collection.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
mutating func popLast() -> Self.Element?
```

Available when `Self` is `Self.SubSequence`.

## Return Value

The last element of the collection if the collection has one or more elements; otherwise, `nil`.

## Discussion

You can use `popLast()` to remove the last element of a collection that might be empty. The `removeLast()` method must be used only on a nonempty collection.

Complexity

O(1)

