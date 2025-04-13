

- Metal Performance Shaders Graph
- MPSGraph
-  reinterpretCast(\_:to:name:) 

Instance Method

# reinterpretCast(\_:to:name:)

Creates a reinterpret cast operation and returns the result tensor.

iOS 16.3+iPadOS 16.3+Mac Catalyst 16.3+macOS 13.2+tvOS 16.3+visionOS 1.0+

``` source
func reinterpretCast(
    _ tensor: MPSGraphTensor,
    to type: MPSDataType,
    name: String?
) -> MPSGraphTensor
```

## Parameters 

`tensor`  

The input tensor.

`type`  

The element type of the returned tensor.

`name`  

The name for the operation.

## Return Value

A valid MPSGraphTensor object.

## Discussion

Returns input tensor (with element type `tensor_type`) reinterpreted to element type passed in with the last dimension scaled by `sizeof(tensor_type) / sizeof(type)`. This operation is endianness agnostic and MPSGraph reinterprets the data with the endianness of the system.

