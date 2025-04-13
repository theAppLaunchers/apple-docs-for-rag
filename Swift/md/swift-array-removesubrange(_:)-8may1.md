

- Swift
- Array
-  removeSubrange(\_:) 

Instance Method

# removeSubrange(\_:)

Removes the elements in the specified subrange from the collection.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
mutating func removeSubrange(_ bounds: Range)
```

## Parameters 

`bounds`  

The range of the collection to be removed. The bounds of the range must be valid indices of the collection.

## Discussion

All the elements following the specified position are moved to close the gap. This example removes three elements from the middle of an array of measurements.

```
var measurements = [1.2, 1.5, 2.9, 1.2, 1.5]
measurements.removeSubrange(1..

Calling this method may invalidate any existing indices for use with this collection.

Complexity

O(*n*), where *n* is the length of the collection.

## See Also

### Removing Elements

func remove(at: Int) -> Element

Removes and returns the element at the specified position.

func removeFirst() -> Self.Element

Removes and returns the first element of the collection.

func removeFirst(Int)

Removes the specified number of elements from the beginning of the collection.

func removeLast() -> Self.Element

Removes and returns the last element of the collection.

func removeLast(Int)

Removes the specified number of elements from the end of the collection.

func removeSubrange&lt;R>(R)

Removes the elements in the specified subrange from the collection.

func removeAll(where: (Self.Element) throws -> Bool) rethrows

Removes all the elements that satisfy the given predicate.

func removeAll(keepingCapacity: Bool)

Removes all elements from the array.

func popLast() -> Self.Element?

Removes and returns the last element of the collection.

