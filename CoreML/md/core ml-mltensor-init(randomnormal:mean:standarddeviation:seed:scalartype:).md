

- Core ML
- MLTensor
-  init(randomNormal:mean:standardDeviation:seed:scalarType:) 

Initializer

# init(randomNormal:mean:standardDeviation:seed:scalarType:)

Creates a tensor with the specified shape, randomly sampling scalar values from a normal distribution.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
init(
    randomNormal shape: [Int],
    mean: Scalar = Scalar.init(0.0),
    standardDeviation: Scalar = Scalar.init(1.0),
    seed: UInt64? = nil,
    scalarType: Scalar.Type = Scalar.self
) where Scalar : MLTensorScalar, Scalar : BinaryFloatingPoint
```

## Parameters 

`shape`  

The shape of the tensor.

`mean`  

The mean of the distribution.

`standardDeviation`  

The standard deviation of the distribution.

`seed`  

The random seed.

`scalarType`  

The scalar type.

## Discussion

Note

Using the same seed produces the same result only when dispatched to the same compute device.

