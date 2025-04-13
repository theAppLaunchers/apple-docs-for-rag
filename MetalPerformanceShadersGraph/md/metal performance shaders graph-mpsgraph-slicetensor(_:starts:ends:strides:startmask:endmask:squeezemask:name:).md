

- Metal Performance Shaders Graph
- MPSGraph
-  sliceTensor(\_:starts:ends:strides:startMask:endMask:squeezeMask:name:) 

Instance Method

# sliceTensor(\_:starts:ends:strides:startMask:endMask:squeezeMask:name:)

Creates a strided-slice operation and returns the result tensor.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+

``` source
func sliceTensor(
    _ tensor: MPSGraphTensor,
    starts: [NSNumber],
    ends: [NSNumber],
    strides: [NSNumber],
    startMask: UInt32,
    endMask: UInt32,
    squeezeMask: UInt32,
    name: String?
) -> MPSGraphTensor
```

## Parameters 

`tensor`  

The Tensor to be sliced.

`starts`  

An array of numbers that specify the starting points for each dimension.

`ends`  

An array of numbers that specify the ending points for each dimension.

`strides`  

An array of numbers that specify the strides for each dimension.

`startMask`  

A bitmask that indicates dimensions whose `starts` values the operation should ignore.

`endMask`  

A bitmask that indicates dimensions whose `ends` values the operation should ignore.

`squeezeMask`  

A bitmask that indicates dimensions the operation will squeeze out from the result.

`name`  

The name for the operation.

## Return Value

A valid MPSGraphTensor object.

## Discussion

Slices a tensor starting from `starts`, stopping short before `ends` stepping `strides` paces between each value. Semantics based on TensorFlow Strided Slice Op.

