

- Accelerate
- vImage
-  vImage buffers 

API Collection

# vImage buffers

Use buffers to pass image data to and from vImage operations.

## Overview

The vImage_Buffer structure is the fundamental data type for passing image data to and from vImage operations.

A vImage buffer describes a rectangular region of pixels and specifies the width, height, number of bytes in each row, and a pointer to the pixel data memory. However, a buffer doesn’t describe image properties, such as pixel format, color space, and channel ordering.

vImage provides functions that initialize buffers from Core Graphics images and Core Video pixel buffers, generate Core Graphics images, and populate Core Video pixel buffers from vImage buffers.

## Topics

### Initializing vImage buffers

struct vImage_Buffer

An image buffer that stores an image’s pixel data, dimensions, and row stride.

func vImageBuffer_Init(UnsafeMutablePointer&lt;vImage_Buffer>, vImagePixelCount, vImagePixelCount, UInt32, vImage_Flags) -> vImage_Error

Initializes a vImage buffer with a specified width, height, and bits per pixel.

### Querying vImage buffer attributes

func vImageBuffer_GetSize(UnsafePointer&lt;vImage_Buffer>) -> CGSize

Returns the size, in pixels, of a vImage buffer.

### Copying vImage buffers

func vImageCopyBuffer(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>, Int, vImage_Flags) -> vImage_Error

Copies the contents of a vImage buffer to a destination buffer.

## See Also

### vImage Buffers

Optimizing image-processing performance

Improve your app’s performance by converting image buffer formats from interleaved to planar.

