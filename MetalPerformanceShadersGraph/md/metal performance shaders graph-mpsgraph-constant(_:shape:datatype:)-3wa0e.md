

- Metal Performance Shaders Graph
- MPSGraph
-  constant(\_:shape:dataType:) 

Instance Method

# constant(\_:shape:dataType:)

Creates a constant op with a given shape and returns the result tensor.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+

``` source
func constant(
    _ scalar: Double,
    shape: [NSNumber],
    dataType: MPSDataType
) -> MPSGraphTensor
```

## Parameters 

`scalar`  

The scalar value to fill the entire tensor values with.

`shape`  

The shape of the output tensor.

`dataType`  

The dataType of the constant tensor.

## Return Value

A valid MPSGraphTensor object.

