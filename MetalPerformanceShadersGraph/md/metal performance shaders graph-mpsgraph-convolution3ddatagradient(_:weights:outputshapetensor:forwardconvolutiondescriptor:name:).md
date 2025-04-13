

- Metal Performance Shaders Graph
- MPSGraph
-  convolution3DDataGradient(\_:weights:outputShapeTensor:forwardConvolutionDescriptor:name:) 

Instance Method

# convolution3DDataGradient(\_:weights:outputShapeTensor:forwardConvolutionDescriptor:name:)

Creates a 3D convolution gradient operation with respect to the source tensor of the forward convolution.

iOS 16.3+iPadOS 16.3+Mac Catalyst 16.3+macOS 13.2+tvOS 16.3+visionOS 1.0+

``` source
func convolution3DDataGradient(
    _ gradient: MPSGraphTensor,
    weights: MPSGraphTensor,
    outputShapeTensor: MPSGraphTensor,
    forwardConvolutionDescriptor: MPSGraphConvolution3DOpDescriptor,
    name: String?
) -> MPSGraphTensor
```

## Parameters 

`weights`  

Forward pass weights tensor

`outputShapeTensor`  

4D Int32 or Int64 tensor. Shape of the forward pass source tensor

`forwardConvolutionDescriptor`  

Forward convolution 2D op `descriptor`

`name`  

The name for the operation.

## Return Value

A valid MPSGraphTensor object

## Discussion

If `S` is source tensor to forward convolution, `R` is the result/returned tensor of forward convolution, and `L` is the loss function, convolution3DDataGradientWithIncomingGradientTensor returns tensor `dL/dS = dL/dR * dR/dS`, where `dL/dR` is the incomingGradient parameter.

