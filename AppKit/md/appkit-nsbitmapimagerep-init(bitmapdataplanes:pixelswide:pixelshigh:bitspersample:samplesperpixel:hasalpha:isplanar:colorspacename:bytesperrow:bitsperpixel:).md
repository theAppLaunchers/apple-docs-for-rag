

- AppKit
- NSBitmapImageRep
-  init(bitmapDataPlanes:pixelsWide:pixelsHigh:bitsPerSample:samplesPerPixel:hasAlpha:isPlanar:colorSpaceName:bytesPerRow:bitsPerPixel:) 

Initializer

# init(bitmapDataPlanes:pixelsWide:pixelsHigh:bitsPerSample:samplesPerPixel:hasAlpha:isPlanar:colorSpaceName:bytesPerRow:bitsPerPixel:)

Initializes a newly allocated bitmap image representation so it can render the specified image.

macOS

``` source
init?(
    bitmapDataPlanes planes: UnsafeMutablePointer?>?,
    pixelsWide width: Int,
    pixelsHigh height: Int,
    bitsPerSample bps: Int,
    samplesPerPixel spp: Int,
    hasAlpha alpha: Bool,
    isPlanar: Bool,
    colorSpaceName: NSColorSpaceName,
    bytesPerRow rBytes: Int,
    bitsPerPixel pBits: Int
)
```

## Parameters 

`planes`  

An array of character pointers, each of which points to a buffer containing raw image data. If the data is in planar configuration, each buffer holds one component—one plane—of the data. Color planes are arranged in the standard order—for example, red before green before blue for RGB color. All color planes precede the coverage plane. If a coverage plane exists, the bitmap’s color components must be premultiplied with it. If the data is in meshed configuration (that is, `isPlanar` is false), only the first buffer is read.

If `planes` is `NULL` or an array of `NULL` pointers, this method allocates enough memory to hold the image described by the other arguments. You can then obtain pointers to this memory (with the getPixel(_:atX:y:) method or bitmapData property) and fill in the image data. In this case, the allocated memory will belong to the object and will be freed when it’s freed.

If `planes` is not `NULL` and the array contains at least one data pointer, the returned object will only reference the image data; it will not copy it. The object treats the image data in the buffers as immutable and will not attempt to alter it. When the object itself is freed, it will not attempt to free the buffers.

`width`  

The width of the image in pixels. This value must be greater than 0.

`height`  

The height of the image in pixels. This value must be greater than 0.

`bps`  

The number of bits used to specify one pixel in a single component of the data. All components are assumed to have the same bits per sample. `bps` should be one of these values: 1, 2, 4, 8, 12, or 16.

`spp`  

The number of data components, or samples per pixel. This value includes both color components and the coverage component (alpha), if present. Meaningful values range from 1 through 5. An image with cyan, magenta, yellow, and black (CMYK) color components plus a coverage component would have an `spp` of 5; a grayscale image that lacks a coverage component would have an `spp` of 1.

`alpha`  

true if one of the components counted in the number of samples per pixel (`spp`) is a coverage (alpha) component, and false if there is no coverage component. If true, the color components in the bitmap data must be premultiplied with their coverage component.

`isPlanar`  

true if the data components are laid out in a series of separate “planes” or channels (“planar configuration”) and false if component values are interwoven in a single channel (“meshed configuration”). If false, only the first buffer of `planes` is read.

For example, in meshed configuration, the red, green, blue, and coverage values for the first pixel of an image would precede the red, green, blue, and coverage values for the second pixel, and so on. In planar configuration, red values for all the pixels in the image would precede all green values, which would precede all blue values, which would precede all coverage values.

`colorSpaceName`  

A constant that indicates how data values are to be interpreted. It should be one of the constants in NSColorSpaceName.

If `bps` is 12, you cannot specify the monochrome color space.

`rBytes`  

The number of bytes that are allocated for each scan line in each plane of data. A scan line is a single row of pixels spanning the width of the image.

Normally, `rowBytes` can be figured from the width of the image, the number of bits per pixel in each sample (`bps`), and, if the data is in a meshed configuration, the number of samples per pixel (`spp`). However, if the data for each row is aligned on word or other boundaries, it may have been necessary to allocate more memory for each row than there is data to fill it. `rowBytes` lets the object know whether that’s the case.

If you pass in a `rowBytes` value of 0, the bitmap data allocated may be padded to fall on long word or larger boundaries for performance. If your code wants to advance row by row, use bytesPerRow and do not assume the data is packed. Passing in a non-zero value allows you to specify exact row advances.

`pBits`  

This integer value informs NSBitmapImageRep how many bits are actually allocated per pixel in each plane of data. If the data is in planar configuration, this normally equals `bps` (bits per sample). If the data is in meshed configuration, it normally equals `bps` times `spp` (samples per pixel). However, it’s possible for a pixel specification to be followed by some meaningless bits (empty space), as may happen, for example, if pixel data is aligned on byte boundaries. `NSBitmapImageRep` supports only a limited number of `pixelBits` values (other than the default): for RGB images with 4 `bps`, `pixelBits` may be 16; for RGB images with 8 `bps`, `pixelBits` may be 32. The legal values for `pixelBits` are system dependent.

If you specify 0 for this parameter, the object interprets the number of bits per pixel using the values in the `bps` and `spp` parameters, as described in the preceding paragraph, without any meaningless bits.

## Return Value

An initialized NSBitmapImageRep object or `nil` if the object cannot be initialized.

## See Also

### Creating Bitmap Representations of Images

class func imageReps(with: Data) -> [NSImageRep]

Creates and returns an array of bitmap image representation objects that correspond to the images in the specified data.

func colorize(byMappingGray: CGFloat, to: NSColor?, blackMapping: NSColor?, whiteMapping: NSColor?)

Colorizes a grayscale image.

init?(bitmapDataPlanes: UnsafeMutablePointer&lt;UnsafeMutablePointer&lt;UInt8>?>?, pixelsWide: Int, pixelsHigh: Int, bitsPerSample: Int, samplesPerPixel: Int, hasAlpha: Bool, isPlanar: Bool, colorSpaceName: NSColorSpaceName, bitmapFormat: NSBitmapImageRep.Format, bytesPerRow: Int, bitsPerPixel: Int)

Initializes a newly allocated bitmap image representation so it can render the specified image.

init(cgImage: CGImage)

Returns a bitmap image representation from a Core Graphics image object.

init(ciImage: CIImage)

Returns a bitmap image representation from a Core Image object.

init?(data: Data)

Initializes a newly allocated bitmap image representation from the specified data.

init(forIncrementalLoad: ())

Initializes a newly allocated bitmap image representation for incremental loading.

init?(focusedViewRect: NSRect)

Initializes a newly allocated bitmap image representation with bitmap data from a rendered image.

Deprecated

