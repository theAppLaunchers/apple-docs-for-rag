

- Swift
- Slice
-  bindMemory(to:) 

Instance Method

# bindMemory(to:)

Binds this buffer slice’s memory to the specified type and returns a typed buffer of the bound memory.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
@discardableResult
func bindMemory(to type: T.Type) -> UnsafeMutableBufferPointer
```

Available when `Base` is `UnsafeMutableRawBufferPointer`.

## Parameters 

`type`  

The type `T` to bind the memory to.

## Return Value

A typed buffer of the newly bound memory. The memory in this region is bound to `T`, but has not been modified in any other way. The typed buffer references `self.count / MemoryLayout.stride` instances of `T`.

## Discussion

Use the `bindMemory(to:)` method to bind the memory referenced by this buffer slice to the type `T`. The memory must be uninitialized or initialized to a type that is layout compatible with `T`. If the memory is uninitialized, it is still uninitialized after being bound to `T`.

Warning

A memory location may only be bound to one type at a time. The behavior of accessing memory as a type unrelated to its bound type is undefined.

