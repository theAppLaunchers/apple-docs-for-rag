

- Swift
- UnsafeMutableRawBufferPointer
-  storeBytes(of:toByteOffset:as:) 

Instance Method

# storeBytes(of:toByteOffset:as:)

Stores a value’s bytes into the buffer pointer’s raw memory at the specified byte offset.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func storeBytes(
    of value: T,
    toByteOffset offset: Int = 0,
    as type: T.Type
)
```

## Parameters 

`value`  

The value to store as raw bytes.

`offset`  

The offset in bytes into the buffer pointer’s memory to begin writing bytes from the value. The default is zero.

`type`  

The type to use for the newly constructed instance. The memory must be initialized to a value of a type that is layout compatible with `type`.

## Discussion

The type `T` to be stored must be a trivial type. The memory must also be uninitialized, initialized to `T`, or initialized to another trivial type that is layout compatible with `T`.

The memory written to must not extend beyond the buffer pointer’s memory region—that is, `offset + MemoryLayout.size` must be less than or equal to the buffer pointer’s `count`.

After calling `storeBytes(of:toByteOffset:as:)`, the memory is initialized to the raw bytes of `value`. If the memory is bound to a type `U` that is layout compatible with `T`, then it contains a value of type `U`. Calling `storeBytes(of:toByteOffset:as:)` does not change the bound type of the memory.

Note

A trivial type can be copied with just a bit-for-bit copy without any indirection or reference-counting operations. Generally, native Swift types that do not contain strong or weak references or other forms of indirection are trivial, as are imported C structs and enums.

If you need to store into memory a copy of a value of a type that isn’t trivial, you cannot use the `storeBytes(of:toByteOffset:as:)` method. Instead, you must know either initialize the memory or, if you know the memory was already bound to `type`, assign to the memory.

