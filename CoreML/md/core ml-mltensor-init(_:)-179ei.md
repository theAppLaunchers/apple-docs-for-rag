

- Core ML
- MLTensor
-  init(\_:) 

Initializer

# init(\_:)

Creates a tensor from a ML shaped array.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
init(_ shapedArray: ShapedArray) where ShapedArray : MLShapedArrayProtocol, ShapedArray.Scalar : MLTensorScalar
```

## Parameters 

`shapedArray`  

The shaped array.

