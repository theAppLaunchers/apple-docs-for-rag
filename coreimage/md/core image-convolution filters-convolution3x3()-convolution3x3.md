

- Core Image
- Convolution Filters
-  convolution3X3() 

Type Method

# convolution3X3()

Applies a convolution 3 x 3 filter to the `RGBA` components of an image.

iOS 13.0+iPadOS 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+

``` source
class func convolution3X3() -> any CIFilter & CIConvolution
```

## Return Value

The modified image.

## Discussion

This method applies a 3 x 3 convolution to the `RGBA` components of an image. The effect uses a 3 x 3 area surrounding an input pixel, the pixel itself, and those within a distance of 1 pixel horizontally and vertically. The effect repeats this for every pixel within the image. The work area is then combined with the weight property vector to produce the processed image. This filter differs from the convolutionRGB3X3Filter, which only processes the `RGB` color components.

The convolution 3 x 3 filter uses the following properties:

`bias`  
A `float` representing the value that’s added to each output pixel as a NSNumber.

`weights`  
A CIVector representing the convolution kernel.

`inputImage`  
An image with the type CIImage.

Note

When using a nonzero `bias` value, the output image has an infinite extent. You should crop the output image before attempting to render it.

The following code creates a filter that sharpens the input image:

func convolution3X3(inputImage: CIImage) -> CIImage? {
    let convolutionFilter = CIFilter.convolution3X3()
    convolutionFilter.inputImage = inputImage
    let kernel = CIVector(values: [
        0, -2, 0,
        -2, 9, -2,
        0, -2, 0
    ], count: 9)
    convolutionFilter.weights = kernel
    convolutionFilter.bias = 0.0
    return convolutionFilter.outputImage!
}

## See Also

### Filters

class func convolution5X5() -> any CIFilter &amp; CIConvolution

Applies a convolution 5 x 5 filter to the `RGBA` components image.

class func convolution7X7() -> any CIFilter &amp; CIConvolution

Applies a convolution 7 x 7 filter to the `RGBA` color components of an image.

class func convolution9Horizontal() -> any CIFilter &amp; CIConvolution

Applies a convolution-9 horizontal filter to the `RGBA` components of an image.

class func convolution9Vertical() -> any CIFilter &amp; CIConvolution

Applies a convolution-9 vertical filter to the `RGBA` components of an image.

class func convolutionRGB3X3() -> any CIFilter &amp; CIConvolution

Applies a convolution 3 x 3 filter to the `RGB` components of an image.

class func convolutionRGB5X5() -> any CIFilter &amp; CIConvolution

Applies a convolution 5 x 5 filter to the `RGB` components of an image.

class func convolutionRGB7X7() -> any CIFilter &amp; CIConvolution

Applies a convolution 7 x 7 filter to the RGB components of an image.

class func convolutionRGB9Horizontal() -> any CIFilter &amp; CIConvolution

Applies a convolution 9 x 1 filter to the RGB components of an image.

class func convolutionRGB9Vertical() -> any CIFilter &amp; CIConvolution

Applies a convolution 1 x 9 filter to the RGB components of an image.

