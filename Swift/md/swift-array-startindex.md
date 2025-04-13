

- Swift
- Array
-  startIndex 

Instance Property

# startIndex

The position of the first element in a nonempty array.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var startIndex: Int { get }
```

## Discussion

For an instance of `Array`, `startIndex` is always zero. If the array is empty, `startIndex` is equal to `endIndex`.

## See Also

### Manipulating Indices

var endIndex: Int

The array’s “past the end” position—that is, the position one greater than the last valid subscript argument.

func index(after: Int) -> Int

Returns the position immediately after the given index.

func formIndex(after: inout Int)

Replaces the given index with its successor.

func index(before: Int) -> Int

Returns the position immediately before the given index.

func formIndex(before: inout Int)

Replaces the given index with its predecessor.

func index(Int, offsetBy: Int) -> Int

Returns an index that is the specified distance from the given index.

func formIndex(inout Self.Index, offsetBy: Int)

Offsets the given index by the specified distance.

func index(Int, offsetBy: Int, limitedBy: Int) -> Int?

Returns an index that is the specified distance from the given index, unless that distance is beyond a given limiting index.

func formIndex(inout Self.Index, offsetBy: Int, limitedBy: Self.Index) -> Bool

Offsets the given index by the specified distance, or so that it equals the given limiting index.

func distance(from: Int, to: Int) -> Int

Returns the distance between two indices.

