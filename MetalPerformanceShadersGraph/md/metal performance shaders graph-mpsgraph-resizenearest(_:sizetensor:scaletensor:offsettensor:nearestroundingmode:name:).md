

- Metal Performance Shaders Graph
- MPSGraph
-  resizeNearest(\_:sizeTensor:scaleTensor:offsetTensor:nearestRoundingMode:name:) 

Instance Method

# resizeNearest(\_:sizeTensor:scaleTensor:offsetTensor:nearestRoundingMode:name:)

Creates a Resize operation and returns the result tensor.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+

``` source
func resizeNearest(
    _ imagesTensor: MPSGraphTensor,
    sizeTensor size: MPSGraphTensor,
    scaleTensor scale: MPSGraphTensor,
    offsetTensor offset: MPSGraphTensor,
    nearestRoundingMode: MPSGraphResizeNearestRoundingMode,
    name: String?
) -> MPSGraphTensor
```

## Parameters 

`imagesTensor`  

Tensor containing input images.

`size`  

The target size of the result tensor. 1D Int32 or Int64 tensor of size equal to rank of input.

`scale`  

1D float tensor of size equal to rank of input.

`offset`  

1D float tensor of size equal to rank of input.

`nearestRoundingMode`  

The rounding mode to use when using nearest resampling. Default is roundPreferCeil.

`name`  

The name for the operation.

## Return Value

A valid MPSGraphTensor object

## Discussion

Resamples input images to given size using the provided scale and offset and nearest neighbor sampling. Destination indices are computed using

```
dst_indices = (src_indices * scale) + offset
```

For most use cases passing the scale and offset directly is unnecessary, and it is preferable to use the API specifying centerResult and alignCorners.

