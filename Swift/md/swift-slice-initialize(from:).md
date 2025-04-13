

- Swift
- Slice
-  initialize(from:) 

Instance Method

# initialize(from:)

Initializes the buffer slice’s memory with the given elements.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func initialize(from source: S) -> (unwritten: S.Iterator, index: Slice.Index) where Base == UnsafeMutableBufferPointer, S : Sequence
```

Available when `Base` conforms to `Collection`.

## Parameters 

`source`  

A sequence of elements with which to initialize the buffer.

## Return Value

An iterator to any elements of `source` that didn’t fit in the buffer, and an index to the next uninitialized element in the buffer.

## Discussion

Prior to calling the `initialize(from:)` method on a buffer slice, the memory it references must be uninitialized, or the `Element` type must be a trivial type. After the call, the memory referenced by the buffer slice up to, but not including, the returned index is initialized. The buffer slice must contain sufficient memory to accommodate `source.underestimatedCount`.

The returned index is the position of the next uninitialized element in the buffer slice, which is one past the last element written. If `source` contains no elements, the returned index is equal to the buffer’s `startIndex`. If `source` contains an equal or greater number of elements than the buffer slice can hold, the returned index is equal to the buffer’s `endIndex`.

