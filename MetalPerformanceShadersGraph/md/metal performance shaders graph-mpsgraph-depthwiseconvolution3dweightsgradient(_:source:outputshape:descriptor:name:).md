

- Metal Performance Shaders Graph
- MPSGraph
-  depthwiseConvolution3DWeightsGradient(\_:source:outputShape:descriptor:name:) 

Instance Method

# depthwiseConvolution3DWeightsGradient(\_:source:outputShape:descriptor:name:)

Creates a 3D depthwise convolution gradient for weights operation and returns the result tensor.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+

``` source
func depthwiseConvolution3DWeightsGradient(
    _ incomingGradient: MPSGraphTensor,
    source: MPSGraphTensor,
    outputShape: [NSNumber],
    descriptor: MPSGraphDepthwiseConvolution3DOpDescriptor,
    name: String?
) -> MPSGraphTensor
```

## Parameters 

`incomingGradient`  

A 3D input gradient tensor - must be at least rank=4 (NCDHW).

`source`  

The forward pass 3D Image source as tensor - must be at least rank=4 (NCDHW).

`outputShape`  

The shape of the οutput tensor (and therefore weight tensor of forward pass).

`descriptor`  

The descriptor object that specifies strides, dilation rates and paddings.

`name`  

The name for the operation.

## Return Value

A valid MPSGraphTensor object

