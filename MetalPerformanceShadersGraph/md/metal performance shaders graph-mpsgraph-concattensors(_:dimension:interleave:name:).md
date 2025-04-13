

- Metal Performance Shaders Graph
- MPSGraph
-  concatTensors(\_:dimension:interleave:name:) 

Instance Method

# concatTensors(\_:dimension:interleave:name:)

Creates a concatenation operation and returns the result tensor.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+

``` source
func concatTensors(
    _ tensors: [MPSGraphTensor],
    dimension dimensionIndex: Int,
    interleave: Bool,
    name: String?
) -> MPSGraphTensor
```

## Parameters 

`tensors`  

The tensors to concatenate.

`dimensionIndex`  

The dimension to concatenate across, must be in range: `-rank 

`interleave`  

A boolean value that specifies whether the operation interleaves input tensors.

`name`  

The name for the operation.

## Return Value

A valid MPSGraphTensor object.

## Discussion

Concatenates all input tensors along specified dimension. All inputs must be broadcast compatible along all other dimensions, and have the same type. When interleave is specified, all tensors will be interleaved. To interleave, make sure to provide broadcast compatible inputs along the specified dimension as well. For example:

```
  operand0 = [1, 2, 3]
  operand1 = [4, 5, 6]
  concat([operand0, operand1], axis = 0, interleave = YES) = [1, 4, 2, 5, 3, 6]
```

