

- Swift
- UnsafeMutableBufferPointer
-  initialize(fromContentsOf:) 

Instance Method

# initialize(fromContentsOf:)

Initializes the buffer’s memory with every element of the source.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func initialize(fromContentsOf source: some Collection) -> UnsafeMutableBufferPointer.Index
```

## Parameters 

`source`  

A collection of elements to be used to initialize the buffer’s storage.

## Return Value

The index one past the last element of the buffer initialized by this function.

## Discussion

Prior to calling the `initialize(fromContentsOf:)` method on a buffer, the memory referenced by the buffer must be uninitialized, or the `Element` type must be a trivial type. After the call, the memory referenced by the buffer up to, but not including, the returned index is initialized. The buffer must reference enough memory to accommodate `source.count` elements.

The returned index is the position of the next uninitialized element in the buffer, one past the index of the last element written. If `source` contains no elements, the returned index is equal to the buffer’s `startIndex`. If `source` contains as many elements as the buffer can hold, the returned index is equal to the buffer’s `endIndex`.

Precondition

`self.count` \>= `source.count`

Note

The memory regions referenced by `source` and this buffer must not overlap.

