

- Foundation
- NSIndexSet
-  enumerateRanges(in:options:using:) 

Instance Method

# enumerateRanges(in:options:using:)

Enumerates over the ranges in the range of objects using the block

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func enumerateRanges(
    in range: NSRange,
    options opts: NSEnumerationOptions = [],
    using block: (NSRange, UnsafeMutablePointer) -> Void
)
```

## Parameters 

`range`  

The range of items to enumerate. If the range intersects a range of the receiver’s indexes, then that intersection will be passed to the block.

`opts`  

A bitmask that specifies the NSEnumerationOptions for the enumeration.

`block`  

The block to apply to elements in the index set.

The block takes two arguments:

range  
The range of elements.

stop  
A reference to a Boolean value. The block can set the value to true to stop further processing of the array. The stop argument is an out-only argument. You should only ever set this Boolean to true within the Block.

## Discussion

By default, the enumeration starts with the first object and continues serially through the indexed set range to the last object in the range. You can specify `NSEnumerationConcurrent` and/or `NSEnumerationReverse` as enumeration options to modify this behavior.

This method executes synchronously.

Important

If the Block parameter is `nil` this method will raise an exception.

## See Also

### Enumerating Index Set Content

func enumerateRanges((NSRange, UnsafeMutablePointer&lt;ObjCBool>) -> Void)

Executes a given block using each object in the index set, in the specified ranges.

func enumerateRanges(options: NSEnumerationOptions, using: (NSRange, UnsafeMutablePointer&lt;ObjCBool>) -> Void)

Executes a given block using each object in the index set, in the specified ranges.

