

- Core ML
- MLTensor
-  concatenated(with:alongAxis:) 

Instance Method

# concatenated(with:alongAxis:)

Returns a concatenated tensor along the specified axis.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
func concatenated(
    with other: MLTensor,
    alongAxis axis: Int = 0
) -> MLTensor
```

## Parameters 

`other`  

The tensor to concatenate. The tensors must have the same dimensions, except for the specified axis.

`axis`  

The axis along which to concatenate. Negative values wrap around but must be in the range `[-rank, rank)`.

