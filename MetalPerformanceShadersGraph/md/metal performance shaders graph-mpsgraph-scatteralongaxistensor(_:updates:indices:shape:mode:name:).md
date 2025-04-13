

- Metal Performance Shaders Graph
- MPSGraph
-  scatterAlongAxisTensor(\_:updates:indices:shape:mode:name:) 

Instance Method

# scatterAlongAxisTensor(\_:updates:indices:shape:mode:name:)

Creates a ScatterAlongAxis operation and returns the result tensor.

iOS 15.4+iPadOS 15.4+Mac Catalyst 15.4+macOS 12.3+tvOS 15.4+visionOS 1.0+

``` source
func scatterAlongAxisTensor(
    _ axisTensor: MPSGraphTensor,
    updates updatesTensor: MPSGraphTensor,
    indices indicesTensor: MPSGraphTensor,
    shape: [NSNumber],
    mode: MPSGraphScatterMode,
    name: String?
) -> MPSGraphTensor
```

## Parameters 

`axisTensor`  

Scalar Int32 tensor. The axis to scatter to. Negative values wrap around

`updatesTensor`  

The input tensor to scatter values from

`indicesTensor`  

Int32 or Int64 tensor used to index the result tensor.

`mode`  

The type of update to use

`name`  

The name for the operation.

## Return Value

A valid MPSGraphTensor object

## Discussion

Scatter values from `updatesTensor` along the specified `axis` at indices in `indicesTensor` into a result tensor. Values are updated following `mode`. See MPSGraphScatterMode. The shape of `updatesTensor` and `indicesTensor` must match. `shape` must match except at `axis`. The shape of the result tensor is equal to `shape` and initialized with an initial value corresponding to `mode`. If an index is out of bounds of `shape` along `axis` the update value is skipped.

