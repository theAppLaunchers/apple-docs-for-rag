

- Swift
- Slice
-  initializeMemory(as:fromContentsOf:) 

Instance Method

# initializeMemory(as:fromContentsOf:)

Initializes the buffer slice’s memory with every element of the source, binding the initialized memory to the elements’ type.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func initializeMemory(
    as type: C.Element.Type,
    fromContentsOf source: C
) -> UnsafeMutableBufferPointer where C : Collection
```

Available when `Base` is `UnsafeMutableRawBufferPointer`.

## Parameters 

`type`  

The type of element to which this buffer’s memory will be bound.

`source`  

A collection of elements to be used to initialize the buffer slice’s storage.

## Return Value

A typed buffer referencing the initialized elements. The returned buffer references memory starting at the same base address as this slice, and its count is equal to `source.count`

## Discussion

When calling the `initializeMemory(as:fromContentsOf:)` method, the memory referenced by the buffer slice must be uninitialized, or initialized to a trivial type. The buffer slice must reference enough memory to store `source.count` elements, and it must be properly aligned for accessing `C.Element`.

This method initializes the buffer with the contents of `source` until `source` is exhausted. After calling `initializeMemory(as:fromContentsOf:)`, the memory referenced by the returned `UnsafeMutableBufferPointer` instance is bound to the type of `C.Element` and is initialized. This method does not change the binding state of the unused portion of the buffer slice, if any.

