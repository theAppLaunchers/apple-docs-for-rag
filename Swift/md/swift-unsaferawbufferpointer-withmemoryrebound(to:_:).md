

- Swift
- UnsafeRawBufferPointer
-  withMemoryRebound(to:\_:) 

Instance Method

# withMemoryRebound(to:\_:)

Executes the given closure while temporarily binding the buffer to instances of type `T`.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func withMemoryRebound(
    to type: T.Type,
    _ body: (UnsafeBufferPointer) throws(E) -> Result
) throws(E) -> Result where E : Error, T : ~Copyable, Result : ~Copyable
```

## Parameters 

`type`  

The type to temporarily bind the memory referenced by this buffer.

`body`  

A closure that takes a typed pointer to the same memory as this pointer, only bound to type `T`. The closure’s pointer argument is valid only for the duration of the closure’s execution. If `body` has a return value, that value is also used as the return value for the `withMemoryRebound(to:capacity:_:)` method.

## Return Value

The return value, if any, of the `body` closure parameter.

## Discussion

Use this method when you have a buffer to raw memory and you need to access that memory as instances of a given type `T`. Accessing memory as a type `T` requires that the memory be bound to that type. A memory location may only be bound to one type at a time, so accessing the same memory as an unrelated type without first rebinding the memory is undefined.

Any instance of `T` within the re-bound region may be initialized or uninitialized. The memory underlying any individual instance of `T` must have the same initialization state (i.e. initialized or uninitialized.) Accessing a `T` whose underlying memory is in a mixed initialization state shall be undefined behaviour.

If the byte count of the original buffer is not a multiple of the stride of `T`, then the re-bound buffer is shorter than the original buffer.

After executing `body`, this method rebinds memory back to its original binding state. This can be unbound memory, or bound to a different type.

Note

The buffer’s base address must match the alignment of `T` (as reported by `MemoryLayout.alignment`). That is, `Int(bitPattern: self.baseAddress) % MemoryLayout.alignment` must equal zero.

Note

A raw buffer may represent memory that has been bound to a type. If that is the case, then `T` must be layout compatible with the type to which the memory has been bound. This requirement does not apply if the raw buffer represents memory that has not been bound to any type.

