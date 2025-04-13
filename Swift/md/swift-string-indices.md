

- Swift
- String
-  indices 

Instance Property

# indices

The indices that are valid for subscripting the collection, in ascending order.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var indices: DefaultIndices { get }
```

Available when `Indices` is `DefaultIndices`.

## Discussion

A collection’s `indices` property can hold a strong reference to the collection itself, causing the collection to be non-uniquely referenced. If you mutate the collection while iterating over its indices, a strong reference can cause an unexpected copy of the collection. To avoid the unexpected copy, use the `index(after:)` method starting with `startIndex` to produce indices instead.

```
var c = MyFancyCollection([10, 20, 30, 40, 50])
var i = c.startIndex
while i != c.endIndex {
    c[i] /= 5
    i = c.index(after: i)
}
// c == MyFancyCollection([2, 4, 6, 8, 10])
```

## See Also

### Manipulating Indices

var startIndex: String.Index

The position of the first character in a nonempty string.

var endIndex: String.Index

A string’s “past the end” position—that is, the position one greater than the last valid subscript argument.

func index(after: String.Index) -> String.Index

Returns the position immediately after the given index.

func formIndex(after: inout Self.Index)

Replaces the given index with its successor.

func index(before: String.Index) -> String.Index

Returns the position immediately before the given index.

func formIndex(before: inout Self.Index)

Replaces the given index with its predecessor.

func index(String.Index, offsetBy: Int) -> String.Index

Returns an index that is the specified distance from the given index.

func index(String.Index, offsetBy: Int, limitedBy: String.Index) -> String.Index?

Returns an index that is the specified distance from the given index, unless that distance is beyond a given limiting index.

func formIndex(inout Self.Index, offsetBy: Int)

Offsets the given index by the specified distance.

func formIndex(inout Self.Index, offsetBy: Int, limitedBy: Self.Index) -> Bool

Offsets the given index by the specified distance, or so that it equals the given limiting index.

func distance(from: String.Index, to: String.Index) -> Int

Returns the distance between two indices.

