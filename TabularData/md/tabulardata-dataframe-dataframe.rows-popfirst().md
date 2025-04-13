

- TabularData
- DataFrame
- DataFrame.Rows
-  popFirst() 

Instance Method

# popFirst()

Removes and returns the first element of the collection.

TabularDataSwiftiOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
mutating func popFirst() -> Self.Element?
```

Available when `Self` is `Self.SubSequence`.

## Return Value

The first element of the collection if the collection is not empty; otherwise, `nil`.

## Discussion

Complexity

O(1)

## See Also

### Removing Elements

func popLast() -> Self.Element?

Removes and returns the last element of the collection.

func removeFirst() -> Self.Element

Removes and returns the first element of the collection.

func removeFirst(Int)

Removes the specified number of elements from the beginning of the collection.

func removeLast() -> Self.Element

Removes and returns the last element of the collection.

func removeLast(Int)

Removes the given number of elements from the end of the collection.

