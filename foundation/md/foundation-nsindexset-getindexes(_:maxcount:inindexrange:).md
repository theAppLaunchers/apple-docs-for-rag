

- Foundation
- NSIndexSet
-  getIndexes(\_:maxCount:inIndexRange:) 

Instance Method

# getIndexes(\_:maxCount:inIndexRange:)

The index set fills an index buffer with the indexes contained both in the index set and in an index range, returning the number of indexes copied.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func getIndexes(
    _ indexBuffer: UnsafeMutablePointer,
    maxCount bufferSize: Int,
    inIndexRange range: NSRangePointer?
) -> Int
```

## Parameters 

`indexBuffer`  

Index buffer to fill.

`bufferSize`  

Maximum size of `indexBuffer`.

`range`  

Index range to compare with indexes in the index set; `nil` represents all the indexes in the index set. Indexes in the index range and in the index set are copied to `indexBuffer`. On output, the range of indexes not copied to `indexBuffer`.

## Return Value

Number of indexes placed in `indexBuffer`.

## Discussion

You are responsible for allocating the memory required for `indexBuffer` and for releasing it later.

Suppose you have an index set with contiguous indexes from 1 to 100. If you use this method to request a range of `(1, 100)`—which represents the set of indexes 1 through 100—and specify a buffer size of `20`, this method returns 20 indexes—1 through 20—in `indexBuffer` and sets `indexRange` to `(21, 80)`—which represents the indexes 21 through 100.

Use this method to retrieve entries quickly and efficiently from an index set. You can call this method repeatedly to retrieve blocks of index values and then process them. When doing so, use the return value and `indexRange` to determine when you have finished processing the desired indexes. When the return value is less than `bufferSize`, you have reached the end of the range.

## See Also

### Getting Indexes

var firstIndex: Int

The first index in the index set.

var lastIndex: Int

The last index in the index set.

func indexLessThanIndex(Int) -> Int

Returns either the closest index in the index set that is less than a specific index or the not-found indicator.

func indexLessThanOrEqual(to: Int) -> Int

Returns either the closest index in the index set that is less than or equal to a specific index or the not-found indicator.

func indexGreaterThanOrEqual(to: Int) -> Int

Returns either the closest index in the index set that is greater than or equal to a specific index or the not-found indicator.

func indexGreaterThanIndex(Int) -> Int

Returns either the closest index in the index set that is greater than a specific index or the not-found indicator.

