

- Metal Performance Shaders Graph
- MPSGraph
-  sign(with:name:) 

Instance Method

# sign(with:name:)

Returns the sign of the input tensor elements.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+

``` source
func sign(
    with tensor: MPSGraphTensor,
    name: String?
) -> MPSGraphTensor
```

## Parameters 

`tensor`  

The input tensor.

`name`  

An optional string which serves as an identifier for the operation.

## Return Value

A valid `MPSGraphTensor` object containing the elementwise result of the applied operation.

## Discussion

This operation returns 1.0 if the correspnding input element is greater than 0, -1.0 if it is lesser than 0, -0.0 if it is equal to -0.0, and +0.0 if it is equal to +0.0.

