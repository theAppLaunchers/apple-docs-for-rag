

- Accelerate
- vImage
- vImage Operations
- Applying a flood fill to an image
-  Applying flood fills to an image 

Article

# Applying flood fills to an image

Fill consistently colored connected parts of an image with a new color.

## Overview

The vImage library provides a set of functions that allow you to flood fill areas of an image with a new color. The following image demonstrates how the flood-fill operation can colorize a hand-drawn line illustration:

The flood-fill functions fill areas with identical pixel values. The process of applying lossy compression, such as when generating JPG images, may subtly change pixel values. Use losslessly compressed or uncompressed images, such as PNGs, to achieve the best flood-fill results.

### Create the planar vImage buffer that represents the source image

Create a 32-bit-per-pixel, planar image to store the image of the line drawing.

```
var cgImageFormatPlanarF = vImage_CGImageFormat(
    bitsPerComponent: 32,
    bitsPerPixel: 32,
    colorSpace: CGColorSpaceCreateDeviceGray(),
    bitmapInfo: CGBitmapInfo(
        rawValue: kCGBitmapByteOrder32Host.rawValue |
        CGBitmapInfo.floatComponents.rawValue |
        CGImageAlphaInfo.none.rawValue),
    renderingIntent: .defaultIntent)!

let image: CGImage = [ ... ]

let bufferPlanarF = try! vImage.PixelBuffer(
    cgImage: image,
    cgImageFormat: &cgImageFormatPlanarF)

```

Call the colorThreshold(_:destination:) function to binarize the image, that is, reduce it to only black and white colors with no midtones. Pass a threshold value of `0.5` to convert all pixel values below `0.5` to `0.0`, and other pixel values to `1.0`.

```
bufferPlanarF.colorThreshold(
    0.5,
    destination: bufferPlanarF)
```

### Create the interleaved vImage buffer that represents the destination image

Use the 32-bit planar buffer to create a four-channel, 8-bit-per-pixel buffer.

```
let bufferRGB8 = vImage.PixelBuffer(
    planarBuffers: [bufferPlanarF, bufferPlanarF, bufferPlanarF, bufferPlanarF])
```

### Apply the flood-fill operation

The source image is 1024 pixels wide and 1585 pixels high. The following image shows the coordinates of the six seed pixels:

Call vImageFloodFill_ARGB8888(_:_:_:_:_:_:_:) to apply different colors to different parts of the line drawing. Note that the vImage flood-fill functions only work in place. That is, a single vImage buffer is the source and the destination for the flood-fill operation.

```
bufferRGB8.withUnsafePointerToVImageBuffer { src in
    let alpha = UInt8(255)

    var newARGB: [UInt8] = [alpha, 68, 41, 11]
    let seedX: vImagePixelCount = 600
    var seedY: vImagePixelCount = 10
    vImageFloodFill_ARGB8888(src, nil,
                             seedX, seedY,
                             &newARGB, 8, 0)

    newARGB = [alpha, 160, 198, 212]
    seedY = 200
    vImageFloodFill_ARGB8888(src, nil,
                             seedX, seedY,
                             &newARGB, 8, 0)

    newARGB = [alpha, 147, 163, 169]
    seedY = 450
    vImageFloodFill_ARGB8888(src, nil,
                             seedX, seedY,
                             &newARGB, 8, 0)

    newARGB = [alpha, 90, 101, 103]
    seedY = 700
    vImageFloodFill_ARGB8888(src, nil,
                             seedX, seedY,
                             &newARGB, 8, 0)

    newARGB = [alpha, 54, 62, 65]
    seedY = 900
    vImageFloodFill_ARGB8888(src, nil,
                             seedX, seedY,
                             &newARGB, 8, 0)

    newARGB = [alpha, 51, 81, 28]
    seedY = 1300
    vImageFloodFill_ARGB8888(src, nil,
                             seedX, seedY,
                             &newARGB, 8, 0)
}

```

### Create a Core Graphics image of the result

Create a vImage_CGImageFormat structure that describes the four-channel, 8-bit-per-channel output image.

```
let cgImageFormatRGB8 = vImage_CGImageFormat(
    bitsPerComponent: 8,
    bitsPerPixel: 8 * 4,
    colorSpace: CGColorSpaceCreateDeviceRGB(),
    bitmapInfo: CGBitmapInfo(
        rawValue: CGImageAlphaInfo.noneSkipFirst.rawValue),
    renderingIntent: .defaultIntent)!

```

Finally, call makeCGImage(cgImageFormat:) to generate the image.

```
let result = bufferRGB8.makeCGImage(cgImageFormat: cgImageFormatRGB8)
```

## See Also

### Flood-filling buffers

func vImageFloodFill_Planar8(UnsafePointer&lt;vImage_Buffer>, UnsafeMutableRawPointer!, vImagePixelCount, vImagePixelCount, Pixel_8, Int32, vImage_Flags) -> vImage_Error

Applies a flood-fill operation to an 8-bit planar image.

func vImageFloodFill_Planar16U(UnsafePointer&lt;vImage_Buffer>, UnsafeMutableRawPointer!, vImagePixelCount, vImagePixelCount, Pixel_16U, Int32, vImage_Flags) -> vImage_Error

Applies a flood fill-operation to an unsigned 16-bit planar image.

func vImageFloodFill_ARGB8888(UnsafePointer&lt;vImage_Buffer>, UnsafeMutableRawPointer!, vImagePixelCount, vImagePixelCount, UnsafeMutablePointer&lt;UInt8>!, Int32, vImage_Flags) -> vImage_Error

Applies a flood-fill operation to an 8-bit-per-channel, four-channel interleaved image.

func vImageFloodFill_ARGB16U(UnsafePointer&lt;vImage_Buffer>, UnsafeMutableRawPointer!, vImagePixelCount, vImagePixelCount, UnsafeMutablePointer&lt;UInt16>!, Int32, vImage_Flags) -> vImage_Error

Applies a flood-fill operation to an unsigned 16-bit-per-channel, four-channel interleaved image.

