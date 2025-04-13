

- Metal Performance Shaders
- Image Filters
-  MPSImageConversion 

Class

# MPSImageConversion

A filter that performs a conversion of color space, alpha, or pixel format.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.0+macOS 10.13+tvOS 10.0+visionOS 1.0+

``` source
class MPSImageConversion : MPSUnaryImageKernel
```

## Overview

An `MPSImageConversion` filter allows you to change the alpha encoding or color space of an image. For example, you can convert an image with a premultiplied alpha to non-premultiplied, or change the color space from one variant to another.

As with all Metal Performance Shaders filters, the conversion filter allows for source and destination textures with different pixel formats and, in that case, will convert the source texture's format to the destination texture's format. See Supported Pixel Formats for Image Kernels for a list of supported pixel formats.

Listing 1 shows how you can create an image conversion filter to map the color intensity from the sRGB color space to a linear gamma curve.

guard let srcColorSpace = CGColorSpace(name: CGColorSpace.sRGB),
    let dstColorSpace = CGColorSpace(name: CGColorSpace.linearSRGB),
    let device = MTLCreateSystemDefaultDevice() else {
        return
}

let conversionInfo = CGColorConversionInfo(src: srcColorSpace,
                                           dst: dstColorSpace)

let conversion = MPSImageConversion(device: device,
                                    srcAlpha: .alphaIsOne,
                                    destAlpha: .alphaIsOne,
                                    backgroundColor: nil,
                                    conversionInfo: conversionInfo)

Listing 1 Mapping color intensity from the sRGB color space to a linear gamma curve.

## Topics

### Methods

init(device: any MTLDevice, srcAlpha: MPSAlphaType, destAlpha: MPSAlphaType, backgroundColor: UnsafeMutablePointer&lt;CGFloat>?, conversionInfo: CGColorConversionInfo?)

Initializes a filter that can convert texture color space, alpha, and pixel format.

enum MPSAlphaType

Premultiplication description for the color channels of an image.

### Properties

var sourceAlpha: MPSAlphaType

Premultiplication description for the source texture.

var destinationAlpha: MPSAlphaType

Premultiplication description for the destination texture.

## Relationships

### Inherits From

- MPSUnaryImageKernel

## See Also

### Image Manipulation Filters

class MPSImageScale

A filter that resizes and changes the aspect ratio of an image.

class MPSImageLanczosScale

A filter that resizes and changes the aspect ratio of an image using Lanczos resampling.

class MPSImageBilinearScale

A filter that resizes and changes the aspect ratio of an image using Bilinear resampling.

class MPSImageTranspose

A filter that transposes an image.

