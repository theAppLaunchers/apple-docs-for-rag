

- Swift
- UnsafePointer
-  withMemoryRebound(to:capacity:\_:) 

Instance Method

# withMemoryRebound(to:capacity:\_:)

Executes the given closure while temporarily binding memory to the specified number of instances of type `T`.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func withMemoryRebound(
    to type: T.Type,
    capacity count: Int,
    _ body: (UnsafePointer) throws(E) -> Result
) throws(E) -> Result where E : Error, T : ~Copyable, Result : ~Copyable
```

## Parameters 

`type`  

The type to temporarily bind the memory referenced by this pointer. The type `T` must be layout compatible with the pointer’s `Pointee` type.

`count`  

The number of instances of `T` in the re-bound region.

`body`  

A closure that takes a typed pointer to the same memory as this pointer, only bound to type `T`. The closure’s pointer argument is valid only for the duration of the closure’s execution. If `body` has a return value, that value is also used as the return value for the `withMemoryRebound(to:capacity:_:)` method.

## Return Value

The return value, if any, of the `body` closure parameter.

## Discussion

Use this method when you have a pointer to memory bound to one type and you need to access that memory as instances of another type. Accessing memory as a type `T` requires that the memory be bound to that type. A memory location may only be bound to one type at a time, so accessing the same memory as an unrelated type without first rebinding the memory is undefined.

The region of memory that starts at this pointer and covers `count` strides of `T` instances must be bound to `Pointee`. Any instance of `T` within the re-bound region may be initialized or uninitialized. Every instance of `Pointee` overlapping with a given instance of `T` should have the same initialization state (i.e. initialized or uninitialized.) Accessing a `T` whose underlying `Pointee` storage is in a mixed initialization state shall be undefined behaviour.

The following example temporarily rebinds the memory of a `UInt64` pointer to `Int64`, then accesses a property on the signed integer.

```
let uint64Pointer: UnsafePointer = fetchValue()
let isNegative = uint64Pointer.withMemoryRebound(
    to: Int64.self, capacity: 1
) {
    return $0.pointee 

Because this pointer’s memory is no longer bound to its `Pointee` type while the `body` closure executes, do not access memory using the original pointer from within `body`. Instead, use the `body` closure’s pointer argument to access the values in memory as instances of type `T`.

After executing `body`, this method rebinds memory back to the original `Pointee` type.

Note

Only use this method to rebind the pointer’s memory to a type that is layout compatible with the `Pointee` type. The stride of the temporary type (`T`) may be an integer multiple or a whole fraction of `Pointee`’s stride, for example to point to one element of an aggregate. To bind a region of memory to a type that does not match these requirements, convert the pointer to a raw pointer and use the `bindMemory(to:)` method. If `T` and `Pointee` have different alignments, this pointer must be aligned with the larger of the two alignments.

