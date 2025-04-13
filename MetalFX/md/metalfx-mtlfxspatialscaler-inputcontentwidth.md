

- MetalFX
- MTLFXSpatialScaler
-  inputContentWidth 

Instance Property

# inputContentWidth

The width, in pixels, of the region within the color texture the spatial scaler uses as its input.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+

``` source
var inputContentWidth: Int { get set }
```

**Required**

## Discussion

The input content width must be less than or equal to inputWidth.

## See Also

### Configuring the image input

var colorTextureUsage: MTLTextureUsage

The minimal texture usage options that your app’s input color texture must set to apply the spatial scaler.

**Required**

var colorTexture: (any MTLTexture)?

An input color texture you set for the spatial scaler that supports the correct color texture usage options.

**Required**

var inputContentHeight: Int

The height, in pixels, of the region within the color texture the spatial scaler uses as its input.

**Required**

