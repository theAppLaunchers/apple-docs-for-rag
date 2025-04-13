

- Metal Performance Shaders Graph
- MPSGraph
-  scatter(\_:indices:shape:axis:mode:name:) 

Instance Method

# scatter(\_:indices:shape:axis:mode:name:)

Creates a Scatter operation and returns the result tensor.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+

``` source
func scatter(
    _ updatesTensor: MPSGraphTensor,
    indices indicesTensor: MPSGraphTensor,
    shape: [NSNumber],
    axis: Int,
    mode: MPSGraphScatterMode,
    name: String?
) -> MPSGraphTensor
```

## Parameters 

`updatesTensor`  

Tensor containing values to be inserted into the result tensor.

`indicesTensor`  

Tensor containg the result indices to insert values at.

`shape`  

The shape of the result tensor.

`axis`  

The axis of the result tensor to scatter values along.

`mode`  

The type of update to use on the destination.

`name`  

The name for the operation.

## Return Value

A valid MPSGraphTensor object.

## Discussion

Scatters the slices in updatesTensor to the result tensor along the indices in indicesTensor. The scatter is defined as

```
U = updates.rank 
P = res.rank 
res[i_{0},...,i_{axis-1},indices[i_{axis}],i_{axis+1},...,i_{U-1}] = updates[i_{0},...,i_{axis-1},i_{axis},i_{axis+1},...,i_{U-1}] 
```

Collisions will be updated according to mode. The tensors have the following shape requirements

```
U = P 
indices.rank = 1 
updates.shape[0:axis-1] = res.shape[0:axis-1] 
updates.shape[axis] = indices.shape[0] 
updates.shape[axis+1:U] = res.shape[0:P] 
```

