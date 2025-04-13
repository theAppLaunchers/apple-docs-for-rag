

- Swift
- UnsafeMutableRawBufferPointer
-  deallocate() 

Instance Method

# deallocate()

Deallocates the memory block previously allocated at this buffer pointer’s base address.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func deallocate()
```

## Discussion

This buffer pointer’s `baseAddress` must be `nil` or a pointer to a memory block previously returned by a Swift allocation method. If `baseAddress` is `nil`, this function does nothing. Otherwise, the memory must not be initialized or `Pointee` must be a trivial type. This buffer pointer’s byte `count` must be equal to the originally allocated size of the memory block.

