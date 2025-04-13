

- AVFoundation
- AVCapturePhoto
-  pixelBuffer 

Instance Property

# pixelBuffer

The uncompressed or RAW image sample buffer for the photo, if requested.

iOS 11.0+iPadOS 11.0+Mac Catalyst 14.0+macOS 10.15+tvOS 17.0+

``` source
var pixelBuffer: CVPixelBuffer? { get }
```

## Mentioned in 

Capturing Uncompressed Image Data

## Discussion

If you requested photo capture in a RAW format, or in a processed format without compression such as TIFF, you can use this property to access the underlying sample buffer.

If you requested capture in a compressed format such as JPEG or HEVC/HEIF, this property’s value is `nil`. Use the fileDataRepresentation() or cgImageRepresentation() method to obtain compressed image data.

## See Also

### Accessing Photo Pixel Data

var isRawPhoto: Bool

A Boolean value indicating whether this photo object contains RAW format data.

