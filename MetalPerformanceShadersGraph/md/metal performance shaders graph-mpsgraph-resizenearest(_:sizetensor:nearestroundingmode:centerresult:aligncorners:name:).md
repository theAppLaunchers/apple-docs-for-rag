

- Metal Performance Shaders Graph
- MPSGraph
-  resizeNearest(\_:sizeTensor:nearestRoundingMode:centerResult:alignCorners:name:) 

Instance Method

# resizeNearest(\_:sizeTensor:nearestRoundingMode:centerResult:alignCorners:name:)

Creates a Resize operation and returns the result tensor.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+

``` source
func resizeNearest(
    _ imagesTensor: MPSGraphTensor,
    sizeTensor size: MPSGraphTensor,
    nearestRoundingMode: MPSGraphResizeNearestRoundingMode,
    centerResult: Bool,
    alignCorners: Bool,
    name: String?
) -> MPSGraphTensor
```

## Parameters 

`imagesTensor`  

Tensor containing input images.

`size`  

The target size of the result tensor. 1D Int32 or Int64 tensor of size equal to rank of input.

`nearestRoundingMode`  

The rounding mode to use when using nearest resampling. Default is roundPreferCeil.

`centerResult`  

Controls if the result image is centered on the input image. When NO, the result will have the top left corner aligned

`alignCorners`  

When YES, the result image will have the same value as the input image in the corners

`name`  

The name for the operation.

## Return Value

A valid MPSGraphTensor object

## Discussion

Resamples input images to given size using nearest neighbor sampling. Result images will be distorted if size is of different aspect ratio. Destination indices are computed using direct index scaling by default, with no offset added. If the centerResult parameter is true, the destination indices will be scaled and shifted to be centered on the input image. If the alignCorners parameter is true, the corners of the result images will match the input images. Scaling will be modified to a factor of (size - 1) / (inputSize - 1). When alignCorners is true, the centerResult parameter does nothing. In order to achieve the same behavior as OpenCV’s resize and TensorFlowV2’s resize,

```
centerResult = YES;
alginCorners = NO;
```

To achieve the same behavior as TensorFlowV1 resize

```
centerResult = NO;
```

