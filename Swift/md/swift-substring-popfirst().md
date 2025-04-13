

- Swift
- Substring
-  popFirst() 

Instance Method

# popFirst()

Removes and returns the first element of the collection.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
mutating func popFirst() -> Self.Element?
```

Available when `Self` is `Self.SubSequence`.

## Return Value

The first element of the collection if the collection is not empty; otherwise, `nil`.

## Discussion

Complexity

O(1)

