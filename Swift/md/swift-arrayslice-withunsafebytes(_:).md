

- Swift
- ArraySlice
-  withUnsafeBytes(\_:) 

Instance Method

# withUnsafeBytes(\_:)

Calls the given closure with a pointer to the underlying bytes of the array’s contiguous storage.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func withUnsafeBytes(_ body: (UnsafeRawBufferPointer) throws -> R) rethrows -> R
```

## Parameters 

`body`  

A closure with an `UnsafeRawBufferPointer` parameter that points to the contiguous storage for the array. If no such storage exists, it is created. If `body` has a return value, that value is also used as the return value for the `withUnsafeBytes(_:)` method. The argument is valid only for the duration of the closure’s execution.

## Return Value

The return value, if any, of the `body` closure parameter.

## Discussion

The array’s `Element` type must be a *trivial type*, which can be copied with just a bit-for-bit copy without any indirection or reference-counting operations. Generally, native Swift types that do not contain strong or weak references are trivial, as are imported C structs and enums.

The following example copies the bytes of the `numbers` array into a buffer of `UInt8`:

```
var numbers: [Int32] = [1, 2, 3]
var byteBuffer: [UInt8] = []
numbers.withUnsafeBytes {
    byteBuffer.append(contentsOf: $0)
}
// byteBuffer == [1, 0, 0, 0, 2, 0, 0, 0, 3, 0, 0, 0]
```

Note

This example shows the behavior on a little-endian platform.

