

- Core ML
- MLTensor
-  init(stacking:alongAxis:) 

Initializer

# init(stacking:alongAxis:)

Stacks the given tensors along the `axis` dimension into a new tensor with rank one higher than the current tensor and each tensor.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
init(
    stacking tensors: some Collection,
    alongAxis axis: Int = 0
)
```

## Parameters 

`tensors`  

The tensors to stack. All tensors must have the same shape and scalar type.

`axis`  

The axis along which to stack. Negative values wrap around but must be in the range `[-rank, rank]`, where `rank` is the rank of the provided tensors.

## Discussion

Given that `tensors` all have shape `[A, B, C]`, and `tensors.count = N`, then:

- if `axis == 0` then the resulting tensor will have the shape `[N, A, B, C]`.

- if `axis == 1` then the resulting tensor will have the shape `[A, N, B, C]`.

- etc.

For example:

```
// 'x' is [1, 4]
// 'y' is [2, 5]
// 'z' is [3, 6]
MLTensor(stacking: [x, y, z]) // is [[1, 4], [2, 5], [3, 6]]
MLTensor(stacking: [x, y, z], alongAxis: 1) // is [[1, 2, 3], [4, 5, 6]]
```

