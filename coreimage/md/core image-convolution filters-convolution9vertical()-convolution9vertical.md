

- Core Image
- Convolution Filters
-  convolution9Vertical() 

Type Method

# convolution9Vertical()

Applies a convolution-9 vertical filter to the `RGBA` components of an image.

iOS 13.0+iPadOS 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+

``` source
class func convolution9Vertical() -> any CIFilter & CIConvolution
```

## Return Value

The modified image.

## Discussion

This method applies a 1 x 9 convolution filter to the `RGBA` components of an image. The effect uses a 1 x 9 area surrounding an input pixel, the pixel itself, and those within a distance of 4 pixels vertically. The effect repeats this for every pixel within the image. Unlike the convolution filters, which use square matrices, this filter can only produce effects along a vertical axis. You can combine this filter with the convolution9Horizontal() to apply separable 9 x 9 convolutions.

The convolution-9-vertical filter uses the following properties:

`bias`  
A `float` representing the value that’s added to each output pixel as a NSNumber.

`weights`  
A CIVector representing the convolution kernel.

`inputImage`  
An image with the type CIImage.

Note

When using a nonzero `bias` value, the output image has an infinite extent. You should crop the output image before attempting to render it.

The following code creates a filter that detects edges in the input image:

func convolution9Vertical(inputImage: CIImage) -> CIImage? {
    let convolutionFilter = CIFilter.convolution9Vertical()
    convolutionFilter.inputImage = inputImage
    convolutionFilter.inputImage = inputImage
    let weights: [CGFloat] = [1, 1, 1, 1, 1, 1, 1, 1, 1].map { $0/9.0 }
    let kernel = CIVector(values: weights, count: 9)
    convolutionFilter.weights = kernel
    convolutionFilter.bias = 0.0
    return convolutionFilter.outputImage!
}

## See Also

### Filters

class func convolution3X3() -> any CIFilter &amp; CIConvolution

Applies a convolution 3 x 3 filter to the `RGBA` components of an image.

class func convolution5X5() -> any CIFilter &amp; CIConvolution

Applies a convolution 5 x 5 filter to the `RGBA` components image.

class func convolution7X7() -> any CIFilter &amp; CIConvolution

Applies a convolution 7 x 7 filter to the `RGBA` color components of an image.

class func convolution9Horizontal() -> any CIFilter &amp; CIConvolution

Applies a convolution-9 horizontal filter to the `RGBA` components of an image.

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

