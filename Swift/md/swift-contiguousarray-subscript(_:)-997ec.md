

- Swift
- ContiguousArray
-  subscript(\_:) 

Instance Subscript

# subscript(\_:)

Accesses the contiguous subrange of the collection’s elements specified by a range expression.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
subscript(r: R) -> Self.SubSequence where R : RangeExpression, Self.Index == R.Bound { get }
```

## Overview

The range expression is converted to a concrete subrange relative to this collection. For example, using a `PartialRangeFrom` range expression with an array accesses the subrange from the start of the range expression until the end of the array.

```
let streets = ["Adams", "Bryant", "Channing", "Douglas", "Evarts"]
let streetsSlice = streets[2...]
print(streetsSlice)
// ["Channing", "Douglas", "Evarts"]
```

The accessed slice uses the same indices for the same elements as the original collection uses. This example searches `streetsSlice` for one of the strings in the slice, and then uses that index in the original array.

```
let index = streetsSlice.firstIndex(of: "Evarts")    // 4
print(streets[index!])
// "Evarts"
```

Always use the slice’s `startIndex` property instead of assuming that its indices start at a particular value. Attempting to access an element by using an index outside the bounds of the slice’s indices may result in a runtime error, even if that index is valid for the original collection.

```
print(streetsSlice.startIndex)
// 2
print(streetsSlice[2])
// "Channing"

print(streetsSlice[0])
// error: Index out of bounds
```

Complexity

O(1)

