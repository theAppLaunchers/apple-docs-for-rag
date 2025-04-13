

- Core Graphics
- CGImage
-  init(width:height:bitsPerComponent:bitsPerPixel:bytesPerRow:space:bitmapInfo:provider:decode:shouldInterpolate:intent:) 

Initializer

# init(width:height:bitsPerComponent:bitsPerPixel:bytesPerRow:space:bitmapInfo:provider:decode:shouldInterpolate:intent:)

Creates a bitmap image from data supplied by a data provider.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.0+tvOSvisionOS 1.0+watchOS 2.0+

``` source
init?(
    width: Int,
    height: Int,
    bitsPerComponent: Int,
    bitsPerPixel: Int,
    bytesPerRow: Int,
    space: CGColorSpace,
    bitmapInfo: CGBitmapInfo,
    provider: CGDataProvider,
    decode: UnsafePointer?,
    shouldInterpolate: Bool,
    intent: CGColorRenderingIntent
)
```

## Parameters 

`width`  

The width, in pixels, of the required image.

`height`  

The height, in pixels, of the required image

`bitsPerComponent`  

The number of bits for each component in a source pixel. For example, if the source image uses the RGBA-32 format, you would specify 8 bits per component.

`bitsPerPixel`  

The total number of bits in a source pixel. This value must be at least `bitsPerComponent` times the number of components per pixel.

`bytesPerRow`  

The number of bytes of memory for each horizontal row of the bitmap.

`space`  

The color space for the image. The color space is retained; on return, you may safely release it.

`bitmapInfo`  

A constant that specifies whether the bitmap should contain an alpha channel and its relative location in a pixel, along with whether the components are floating-point or integer values.

`provider`  

The source of data for the bitmap. For information about supported data formats, see the discussion below. The provider is retained; on return, you may safely release it.

`decode`  

The decode array for the image. If you do not want to allow remapping of the image’s color values, pass `NULL` for the decode array. For each color component in the image’s color space (including the alpha component), a decode array provides a pair of values denoting the upper and lower limits of a range. For example, the decode array for a source image in the RGB color space would contain six entries total, consisting of one pair each for red, green, and blue. When the image is rendered, Core Graphics uses a linear transform to map the original component value into a relative number within your designated range that is appropriate for the destination color space.

`shouldInterpolate`  

A Boolean value that specifies whether interpolation should occur. The interpolation setting specifies whether Core Graphics should apply a pixel-smoothing algorithm to the image. Without interpolation, the image may appear jagged or pixelated when drawn on an output device with higher resolution than the image data.

`intent`  

A rendering intent constant that specifies how Core Graphics should handle colors that are not located within the gamut of the destination color space of a graphics context. The rendering intent determines the exact method used to map colors from one color space to another. For descriptions of the defined rendering-intent constants, see CGColorRenderingIntent.

## Return Value

A new bitmap image. In Objective-C, you’re responsible for releasing this object by calling CGImageRelease.

## Discussion

The data provider should provide raw data that matches the format specified by the other input parameters. To use encoded data (for example, from a file specified by a URL-based data provider), see init(jpegDataProviderSource:decode:shouldInterpolate:intent:) and init(pngDataProviderSource:decode:shouldInterpolate:intent:).

For information on supported pixel formats, see Quartz 2D Programming Guide.

## See Also

### Creating Images

init?(jpegDataProviderSource: CGDataProvider, decode: UnsafePointer&lt;CGFloat>?, shouldInterpolate: Bool, intent: CGColorRenderingIntent)

Creates a bitmap image using JPEG-encoded data supplied by a data provider.

init?(pngDataProviderSource: CGDataProvider, decode: UnsafePointer&lt;CGFloat>?, shouldInterpolate: Bool, intent: CGColorRenderingIntent)

Creates a bitmap image using PNG-encoded data supplied by a data provider.

init?(headroom: Float, width: Int, height: Int, bitsPerComponent: Int, bitsPerPixel: Int, bytesPerRow: Int, space: CGColorSpace, bitmapInfo: CGBitmapInfo, provider: CGDataProvider, decode: UnsafePointer&lt;CGFloat>?, shouldInterpolate: Bool, intent: CGColorRenderingIntent)

