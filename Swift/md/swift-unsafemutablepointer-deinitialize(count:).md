

- Swift
- UnsafeMutablePointer
-  deinitialize(count:) 

Instance Method

# deinitialize(count:)

Deinitializes the specified number of values starting at this pointer.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
@discardableResult
func deinitialize(count: Int) -> UnsafeMutableRawPointer
```

## Parameters 

`count`  

The number of instances to deinitialize. `count` must not be negative.

## Return Value

A raw pointer to the same address as this pointer. The memory referenced by the returned raw pointer is still bound to `Pointee`.

## Discussion

The region of memory starting at this pointer and covering `count` instances of the pointer’s `Pointee` type must be initialized. After calling `deinitialize(count:)`, the memory is uninitialized, but still bound to the `Pointee` type.

