

- Swift
- LazyMapSequence
-  count 

Instance Property

# count

The number of elements in the collection.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var count: Int { get }
```

Available when `Base` conforms to `Collection`.

## Discussion

To check whether the collection is empty, use its `isEmpty` property instead of comparing `count` to zero. Unless the collection guarantees random-access performance, calculating `count` can be an O(*n*) operation.

Complexity

O(1) if `Index` conforms to `RandomAccessIndex`; O(*n*) otherwise.

