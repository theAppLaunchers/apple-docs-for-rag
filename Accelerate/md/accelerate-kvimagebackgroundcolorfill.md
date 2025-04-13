

- Accelerate
-  kvImageBackgroundColorFill 

Global Variable

# kvImageBackgroundColorFill

A flag that uses the background color for missing pixels.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.3+tvOSvisionOS 1.0+watchOS 2.0+

``` source
var kvImageBackgroundColorFill: Int { get }
```

## Discussion

The associated value is a background color (that is, a pixel value). When you set this flag, vImage assigns the pixel value to all pixels outside the image. You can set this flag for convolution and geometry functions. The morphology functions do not use this flag because they do not use pixels outside the image in any of their calculations.

## See Also

### Edging Modes

var kvImageCopyInPlace: Int

A flag that copies the value of the edge pixel in the source to the destination.

var kvImageEdgeExtend: Int

A flag that extends the edges of the image infinitely.

var kvImageTruncateKernel: Int

A flag that uses only the part of the kernel that overlaps the image.

