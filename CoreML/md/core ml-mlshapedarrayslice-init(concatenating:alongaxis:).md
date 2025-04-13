

- Core ML
- MLShapedArraySlice
-  init(concatenating:alongAxis:) 

Initializer

# init(concatenating:alongAxis:)

Merges a sequence of shaped arrays into one shaped array along an axis.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
init(
    concatenating shapedArrays: S,
    alongAxis: Int
) where Scalar == S.Element.Scalar, S : Sequence, S.Element : MLShapedArrayProtocol
```

## Parameters 

`alongAxis`  

A zero-based axis number the shaped arrays in `multiArray` merge along.

Tip

Select the shaped array’s highest dimension by passing a negative axis number. For example, an axis value of `-1` or `-2` selects the last or second-to-last dimension, respectively.

## Discussion

All shaped arrays in the sequence must have the following:

- The same underlying data type

- The same number of dimensions

- The same size for each corresponding dimension, except for the concatenation axis

For example, this code concatenates two shaped arrays along their second dimension:

```
// A 2x3 shaped array.
// 0 1 2
// 5 6 7
let shapedArray1 = MLShapedArray(scalars: [0, 1, 2, 5, 6, 7],
                                        shape: [2, 3])

// A 2x2 shaped array.
// 3 4
// 8 9
let shapedArray2 = MLShapedArray(scalars: [3, 4, 8, 9],
                                        shape: [2, 2])

// A 2x5 shaped array.
// 0 1 2 3 4
// 5 6 7 8 9
let shapedArray3 = MLShapedArray(concatenating: [shapedArray1,shapedArray2],
                                 alongAxis: 1)
```

## See Also

### Creating a Shaped Array Slice from Another Type

init(MLMultiArray)

Creates a new MLShapedArraySlice using a `MLMultiArray` as a backing storage.

