

- Metal Performance Shaders Graph
- MPSGraph
-  dequantize(\_:LUTTensor:name:) 

Instance Method

# dequantize(\_:LUTTensor:name:)

Creates a lookup-table based quantization operation and returns the result tensor.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+

``` source
func dequantize(
    _ tensor: MPSGraphTensor,
    LUTTensor: MPSGraphTensor,
    name: String?
) -> MPSGraphTensor
```

## Parameters 

`tensor`  

Input tensor to be dequantized.

`LUTTensor`  

The lookup table to use - for u4 the last dimension should have 16 elements, and for u8 256 elements.

`name`  

The name for the operation.

## Return Value

A valid MPSGraphTensor object.

## Discussion

Converts a u8 or u4 `tensor` to a float tensor by applying a lookup operation:

```
result[i1,...,in] = LUTTensor[i1',...,in',tensor[i1,...,in]].
```

Note: The operation supports LUT groups up to the last 3 dimensions for `tensor`.

