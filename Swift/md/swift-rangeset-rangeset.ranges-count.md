

- Swift
- RangeSet
- RangeSet.Ranges
-  count 

Instance Property

# count

The number of elements in the collection.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
var count: Int { get }
```

Available when `Bound` conforms to `Comparable`.

## Discussion

To check whether a collection is empty, use its `isEmpty` property instead of comparing `count` to zero. Unless the collection guarantees random-access performance, calculating `count` can be an O(*n*) operation.

Complexity

O(1) if the collection conforms to `RandomAccessCollection`; otherwise, O(*n*), where *n* is the length of the collection.

