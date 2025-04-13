

- Swift
- Slice
-  deinitialize() 

Instance Method

# deinitialize()

Deinitializes every instance in this buffer slice.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
@discardableResult
func deinitialize() -> UnsafeMutableRawBufferPointer where Base == UnsafeMutableBufferPointer
```

Available when `Base` conforms to `Collection`.

## Return Value

A raw buffer to the same range of memory as this buffer. The range of memory is still bound to `Element`.

## Discussion

The region of memory underlying this buffer slice must be fully initialized. After calling `deinitialize(count:)`, the memory is uninitialized, but still bound to the `Element` type.

Note

All buffer elements must already be initialized.

