

- Metal Performance Shaders Graph
- MPSGraph
-  spaceToBatch(\_:spatialAxesTensor:batchAxisTensor:blockDimensionsTensor:usePixelShuffleOrder:name:) 

Instance Method

# spaceToBatch(\_:spatialAxesTensor:batchAxisTensor:blockDimensionsTensor:usePixelShuffleOrder:name:)

Creates a space-to-batch operation and returns the result tensor.

iOS 16.1+iPadOS 16.1+Mac Catalyst 16.1+macOS 13.0+tvOS 16.1+visionOS 1.0+

``` source
func spaceToBatch(
    _ tensor: MPSGraphTensor,
    spatialAxesTensor: MPSGraphTensor,
    batchAxisTensor: MPSGraphTensor,
    blockDimensionsTensor: MPSGraphTensor,
    usePixelShuffleOrder: Bool,
    name: String?
) -> MPSGraphTensor
```

## Parameters 

`tensor`  

The input tensor.

`spatialAxesTensor`  

A tensor that contains the axes that define the dimensions containing the spatial blocks.

`batchAxisTensor`  

A tensor that contains the axis that defines the destination dimension, where to copy the blocks.

`blockDimensionsTensor`  

A tensor that defines the size of the rectangular spatial sub-block.

`usePixelShuffleOrder`  

A parameter that controls layout of the sub-blocks within the batch dimension.

`name`  

The name for the operation.

## Return Value

A valid MPSGraphTensor object.

## Discussion

This operation outputs a copy of the `input` tensor, where values from the `spatialAxesTensor` (for `usePixelShuffleOrder=YES` 1,2 or 3 axes supported, otherwise limited only by `MPSNDArray` rank limitations) dimensions are moved in spatial blocks with rectangular size defined by `blockDimensionsTensor` to the `batchAxisTensor` dimension. Use the `usePixelShuffleOrder` parameter to control how the data within spatial blocks is ordered in the `batchAxisTensor` dimension: with `usePixelShuffleOrder=YES` MPSGraph stores the values of the spatial blocks contiguosly within the `batchAxisTensor` dimension, whereas otherwise they are stored interleaved with existing values in the `batchAxisTensor` dimension. Note: This operation is the inverse of batchToSpace(_:spatialAxesTensor:batchAxisTensor:blockDimensionsTensor:usePixelShuffleOrder:name:). Note: This operation is a generalization of space(toDepth2DTensor:widthAxisTensor:heightAxisTensor:depthAxisTensor:blockSize:usePixelShuffleOrder:name:).

