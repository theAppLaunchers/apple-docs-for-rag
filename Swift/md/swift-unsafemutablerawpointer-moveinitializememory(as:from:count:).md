

- Swift
- UnsafeMutableRawPointer
-  moveInitializeMemory(as:from:count:) 

Instance Method

# moveInitializeMemory(as:from:count:)

Initializes the memory referenced by this pointer with the values starting at the given pointer, binds the memory to the values’ type, deinitializes the source memory, and returns a typed pointer to the newly initialized memory.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
@discardableResult
func moveInitializeMemory(
    as type: T.Type,
    from source: UnsafeMutablePointer,
    count: Int
) -> UnsafeMutablePointer where T : ~Copyable
```

## Parameters 

`type`  

The type to bind this memory to.

`source`  

A pointer to the values to copy. The memory in the region `source..

`count`  

The number of copies of `value` to copy into memory. `count` must not be negative.

## Return Value

A typed pointer to the memory referenced by this raw pointer.

## Discussion

The memory referenced by this pointer must be uninitialized or initialized to a trivial type, and must be properly aligned for accessing `T`.

The memory in the region `source...stride` is bound to type `T` and initialized. If `T` is a nontrivial type, you must eventually deinitialize or move from the values in this region to avoid leaks. Any memory in the region `source..

