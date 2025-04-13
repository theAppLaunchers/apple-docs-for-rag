

- Metal Performance Shaders Graph
- MPSGraph
-  split(\_:numSplits:axis:name:) 

Instance Method

# split(\_:numSplits:axis:name:)

Creates a split operation and returns the result tensor.

iOS 15.4+iPadOS 15.4+Mac Catalyst 15.4+macOS 12.3+tvOS 15.4+visionOS 1.0+

``` source
func split(
    _ tensor: MPSGraphTensor,
    numSplits: Int,
    axis: Int,
    name: String?
) -> [MPSGraphTensor]
```

## Parameters 

`tensor`  

The input tensor.

`numSplits`  

The number of result tensors to split to.

`axis`  

The dimension along which MPSGraph splits the input tensor.

`name`  

The name for the operation.

## Return Value

A valid MPSGraphTensor object.

## Discussion

Splits the input tensor along `axis` into `numsplits` result tensors of equal size. Requires that the lenth of the input along `axis` is divisible by `numSplits`.

