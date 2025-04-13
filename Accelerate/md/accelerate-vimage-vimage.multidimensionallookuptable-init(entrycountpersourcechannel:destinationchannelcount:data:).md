

- Accelerate
- vImage
- vImage.MultidimensionalLookupTable
-  init(entryCountPerSourceChannel:destinationChannelCount:data:) 

Initializer

# init(entryCountPerSourceChannel:destinationChannelCount:data:)

Returns a new multidimensional lookup table.

iOS 16.0+iPadOS 16.0+Mac CatalystmacOS 13.0+tvOS 16.0+visionOSwatchOS 9.0+

``` source
init(
    entryCountPerSourceChannel: [UInt8],
    destinationChannelCount: Int,
    data: T
) where T : AccelerateBuffer, T.Element == UInt16
```

## Parameters 

`entryCountPerSourceChannel`  

An array that contains the number of table entries for each dimension of the lookup table.

`destinationChannelCount`  

The number of destination channels.

`data`  

The lookup table data. The lookup table must contain the product of the values in destinationChannelCount multiplied by destinationChannelCount.

## Discussion

Supply the values in `data` in the range `0 ... 65535`, the function interprets the values as `0 ... 1` by dividing by `65535`.

