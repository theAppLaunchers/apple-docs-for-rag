

- Metal Performance Shaders Graph
- MPSGraph
-  bottomK(\_:axisTensor:kTensor:name:) 

Instance Method

# bottomK(\_:axisTensor:kTensor:name:)

Creates a BottomK operation and returns the result tensor.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+

``` source
func bottomK(
    _ source: MPSGraphTensor,
    axisTensor: MPSGraphTensor,
    kTensor: MPSGraphTensor,
    name: String?
) -> [MPSGraphTensor]
```

## Parameters 

`source`  

Tensor containing source data.

`axisTensor`  

Tensor containing the dimension along which to compute the BottomK values.

`kTensor`  

Tensor of the number of largest values to return.

`name`  

The name for the operation.

## Return Value

A valid MPSGraphTensor array of size 2.

## Discussion

Finds the k smallest values along the minor dimension of the input. The source must have at least k elements along its minor dimension. The first element of the result array corresponds to the bottom values, and the second array corresponds to the indices of the bottom values.

