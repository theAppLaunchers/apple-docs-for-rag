

- Metal Performance Shaders Graph
- MPSGraph
-  depthwiseConvolution3DDataGradient(\_:weights:outputShape:descriptor:name:) 

Instance Method

# depthwiseConvolution3DDataGradient(\_:weights:outputShape:descriptor:name:)

Creates a 3D depthwise convolution gradient for data operation and returns the result tensor.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+

``` source
func depthwiseConvolution3DDataGradient(
    _ incomingGradient: MPSGraphTensor,
    weights: MPSGraphTensor,
    outputShape: [NSNumber]?,
    descriptor: MPSGraphDepthwiseConvolution3DOpDescriptor,
    name: String?
) -> MPSGraphTensor
```

## Parameters 

`incomingGradient`  

A 3D input gradient tensor - must be at least rank=4 (CDHW).

`weights`  

The weights tensor, must be rank=4 - axes are interpreted as CDHW.

`outputShape`  

The shape of the οutput tensor (and therefore input tensor of forward pass).

`descriptor`  

The descriptor object that specifies strides, dilation rates and paddings.

`name`  

The name for the operation.

## Return Value

A valid MPSGraphTensor object

