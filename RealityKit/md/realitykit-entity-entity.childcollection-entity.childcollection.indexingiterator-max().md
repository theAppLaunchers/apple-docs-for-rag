

- RealityKit
- Entity
- Entity.ChildCollection
- Entity.ChildCollection.IndexingIterator
-  max() 

Instance Method

# max()

Returns the maximum element in the sequence.

RealityKitSwiftiOSiPadOSMac CatalystmacOSvisionOS

``` source
@warn_unqualified_access
func max() -> Self.Element?
```

Available when `Element` conforms to `Comparable`.

## Return Value

The sequence’s maximum element. If the sequence has no elements, returns `nil`.

## Discussion

This example finds the largest value in an array of height measurements.

```
let heights = [67.5, 65.7, 64.3, 61.1, 58.5, 60.3, 64.9]
let greatestHeight = heights.max()
print(greatestHeight)
// Prints "Optional(67.5)"
```

Complexity

O(*n*), where *n* is the length of the sequence.

## See Also

### Finding entities

func contains(Self.Element) -> Bool

Returns a Boolean value indicating whether the sequence contains the given element.

func contains(where: (Self.Element) throws -> Bool) rethrows -> Bool

Returns a Boolean value indicating whether the sequence contains an element that satisfies the given predicate.

func allSatisfy((Self.Element) throws -> Bool) rethrows -> Bool

Returns a Boolean value indicating whether every element of a sequence satisfies a given predicate.

func first(where: (Self.Element) throws -> Bool) rethrows -> Self.Element?

Returns the first element of the sequence that satisfies the given predicate.

func max(by: (Self.Element, Self.Element) throws -> Bool) rethrows -> Self.Element?

Returns the maximum element in the sequence, using the given predicate as the comparison between elements.

func min() -> Self.Element?

Returns the minimum element in the sequence.

func min(by: (Self.Element, Self.Element) throws -> Bool) rethrows -> Self.Element?

Returns the minimum element in the sequence, using the given predicate as the comparison between elements.

