

- Metal Performance Shaders Graph
- MPSGraph
-  reshape(\_:shapeTensor:name:) 

Instance Method

# reshape(\_:shapeTensor:name:)

Creates a reshape operation and returns the result tensor.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+

``` source
func reshape(
    _ tensor: MPSGraphTensor,
    shapeTensor: MPSGraphTensor,
    name: String?
) -> MPSGraphTensor
```

## Parameters 

`tensor`  

The tensor to be reshaped.

`shapeTensor`  

A 1D tensor of type `MPSDataTypeInt32` or `MPSDataTypeInt64`, that contains the target shape values.

`name`  

The name for the operation.

## Return Value

A valid MPSGraphTensor object.

## Discussion

This operation reshapes the input tensor to the target shape. The shape tensor must be compatible with the input tensor shape, specifically the volume of the input tensor has to match the volume defined by the shape tensor. The shape tensor is allowed to contain dynamic dimensions (-1) when the result type can be inferred unambiguously.

