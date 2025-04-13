

- MusicKit
- MusicItemCollection
-  index(\_:offsetBy:) 

Instance Method

# index(\_:offsetBy:)

Returns an index that is the specified distance from the given index.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
func index(
    _ i: MusicItemCollection.Index,
    offsetBy distance: Int
) -> MusicItemCollection.Index
```

Available when `MusicItemType` conforms to `MusicItem`.

## Parameters 

`i`  

A valid index of the collection.

`distance`  

The distance to offset `i`. `distance` must not be negative unless the collection conforms to the `BidirectionalCollection` protocol.

## Return Value

An index offset by `distance` from the index `i`. If `distance` is positive, this is the same value as the result of `distance` calls to `index(after:)`. If `distance` is negative, this is the same value as the result of `abs(distance)` calls to `index(before:)`.

## Discussion

The following example obtains an index advanced four positions from a string’s starting index and then prints the character at that position.

```
let s = "Swift"
let i = s.index(s.startIndex, offsetBy: 4)
print(s[i])
// Prints "t"
```

The value passed as `distance` must not offset `i` beyond the bounds of the collection.

Complexity

O(1)

