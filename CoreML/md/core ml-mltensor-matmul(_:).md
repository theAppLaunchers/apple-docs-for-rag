

- Core ML
- MLTensor
-  matmul(\_:) 

Instance Method

# matmul(\_:)

Multiplies two tensors together using matrix multiplication.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
func matmul(_ other: MLTensor) -> MLTensor
```

## Parameters 

`other`  

The right-hand side tensor to be multiplied.

## Return Value

The result of the matrix multiplication.

## Discussion

The specific behaviour is determined by the dimensionality of the inputs, as described below:

- If both tensors are 1-dimensional, the dot-product is returned.

- If the first is 2-dimensional and other 1-dimensional, the matrix-vector product is returned.

- If both have a rank of 2, the matrix-matrix product is returned and when the rank is greater than 2, the batched matrix multiply is returned

For exmaple:

```
let v1 = MLTensor([1.0, 2.0, 3.0, 4.0])
let v2 = MLTensor([5.0, 6.0, 7.0, 8.0])
let v3 = v1.matmul(v2)
v3.shape // is []
await v3.shapedArray(of: Float.self) // is 70.0

let m1 = MLTensor(shape: [2, 3], scalars: [
    1, 2, 3,
    4, 5, 6
], scalarType: Float.self)
let m2 = MLTensor(shape: [3, 2], scalars: [
     7,  8,
     9, 10,
    11, 12
], scalarType: Float.self)
let m3 = t1.matmul(r2)
m3.shape // is [2, 2]
await m3.shapedArray(of: Float.self) // is [[58, 64], [139, 154]]

// Supports broadcasting
let m4 = MLTensor(randomNormal: [3, 1, 1, 4], scalarType: Float.self)
let m5 = MLTensor(randomNormal: [4, 2], scalarType: Float.self)
let m6 = t4.matmul(t5)
m6.shape // is [3, 1, 1, 2]
```

