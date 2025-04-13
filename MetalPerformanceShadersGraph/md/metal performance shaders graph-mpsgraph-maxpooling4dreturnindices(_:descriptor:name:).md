

- Metal Performance Shaders Graph
- MPSGraph
-  maxPooling4DReturnIndices(\_:descriptor:name:) 

Instance Method

# maxPooling4DReturnIndices(\_:descriptor:name:)

Creates a 4D max-pooling operation and returns the result tensor and the corresponding indices tensor.

iOS 15.3+iPadOS 15.3+Mac Catalyst 15.3+macOS 12.2+tvOS 15.3+visionOS 1.0+

``` source
func maxPooling4DReturnIndices(
    _ source: MPSGraphTensor,
    descriptor: MPSGraphPooling4DOpDescriptor,
    name: String?
) -> [MPSGraphTensor]
```

## Parameters 

`source`  

The source tensor on which pooling will be performed.

`descriptor`  

A pooling operation descriptor that specifies pooling window sizes, strides, dilation rates and paddings.

`name`  

The name for the operation.

## Return Value

An array of two MPSGraphTensors. The first tensor holds the result of max pool and the second tensor holds the corresponding indices.

## Discussion

In order to Computes the indices, `returnIndicesMode` of the descriptor must be set. The datatype of indices tensor can be set using `returnIndicesDataType`. If `returnIndicesMode = MPSGraphPoolingReturnIndicesNone` then only the first result MPSGraph returns will be valid and using the second result will assert.

