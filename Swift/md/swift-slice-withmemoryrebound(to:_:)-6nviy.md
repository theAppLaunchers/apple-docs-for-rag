

- Swift
- Slice
-  withMemoryRebound(to:\_:) 

Instance Method

# withMemoryRebound(to:\_:)

Executes the given closure while temporarily binding the memory referenced by this buffer slice to the given type.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func withMemoryRebound(
    to type: T.Type,
    _ body: (UnsafeBufferPointer) throws -> Result
) rethrows -> Result where Base == UnsafeBufferPointer
```

Available when `Base` conforms to `Collection`.

## Parameters 

`type`  

The type to temporarily bind the memory referenced by this buffer slice. The type `T` must be layout compatible with the pointer’s `Element` type.

`body`  

A closure that takes a typed buffer to the same memory as this buffer slice, only bound to type `T`. The buffer parameter contains a number of complete instances of `T` based on the capacity of the original buffer and the stride of `Element`. The closure’s buffer argument is valid only for the duration of the closure’s execution. If `body` has a return value, that value is also used as the return value for the `withMemoryRebound(to:_:)` method.

## Return Value

The return value, if any, of the `body` closure parameter.

## Discussion

Use this method when you have a buffer slice of memory bound to one type and you need to access that memory as a buffer of another type. Accessing memory as type `T` requires that the memory be bound to that type. A memory location may only be bound to one type at a time, so accessing the same memory as an unrelated type without first rebinding the memory is undefined.

The number of instances of `T` referenced by the rebound buffer may be different than the number of instances of `Element` referenced by the original buffer slice. The number of instances of `T` will be calculated at runtime.

Any instance of `T` within the re-bound region may be initialized or uninitialized. Every instance of `Pointee` overlapping with a given instance of `T` should have the same initialization state (i.e. initialized or uninitialized.) Accessing a `T` whose underlying `Pointee` storage is in a mixed initialization state shall be undefined behaviour.

Because this range of memory is no longer bound to its `Element` type while the `body` closure executes, do not access memory using the original buffer slice from within `body`. Instead, use the `body` closure’s buffer argument to access the values in memory as instances of type `T`.

After executing `body`, this method rebinds memory back to the original `Element` type.

Note

Only use this method to rebind the buffer slice’s memory to a type that is layout compatible with the currently bound `Element` type. The stride of the temporary type (`T`) may be an integer multiple or a whole fraction of `Element`’s stride. To bind a region of memory to a type that does not match these requirements, convert the buffer to a raw buffer and use the `withMemoryRebound(to:)` method on the raw buffer. If `T` and `Element` have different alignments, this buffer slice must be aligned with the larger of the two alignments.

