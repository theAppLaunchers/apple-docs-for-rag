

- Image I/O
-  CGImageSourceUpdateDataProvider(\_:\_:\_:) 

Function

# CGImageSourceUpdateDataProvider(\_:\_:\_:)

Updates an incremental image source with a new data provider.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+macOS 10.4+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func CGImageSourceUpdateDataProvider(
    _ isrc: CGImageSource,
    _ provider: CGDataProvider,
    _ final: Bool
)
```

## Parameters 

`isrc`  

The image source to modify.

`provider`  

The new data provider. The new data provider must provide all the previous data supplied to the image source and any additional new data.

`final`  

A Boolean value that indicates whether the `provider` parameter provides the complete data set. Specify `true` if the data is complete or `false` if it isn’t.

## See Also

### Updating an Incremental Image

func CGImageSourceUpdateData(CGImageSource, CFData, Bool)

Updates the data in an incremental image source.

