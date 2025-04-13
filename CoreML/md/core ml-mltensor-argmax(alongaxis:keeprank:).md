

- Core ML
- MLTensor
-  argmax(alongAxis:keepRank:) 

Instance Method

# argmax(alongAxis:keepRank:)

Returns the indices of the maximum values along the specified axis.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
func argmax(
    alongAxis axis: Int,
    keepRank: Bool = false
) -> MLTensor
```

## Parameters 

`axis`  

The axis to reduce.

`keepRank`  

A Boolean indicating whether to keep the reduced axis or not. The default value is `false`.

## Return Value

The reduced tensor.

## Discussion

```
let x = MLTensor(shape: [3, 2], scalars: [2, 3, 4, 5, 6, 7], scalarType: Float.self)
let y = x.argmax(alongAxis: 0)
y.shape // is [2]
y.scalarType // is Int32
await y.shapedArray(of: Int32.self) // is 2 2
```

