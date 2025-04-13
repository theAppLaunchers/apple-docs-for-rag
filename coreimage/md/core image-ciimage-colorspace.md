

- Core Image
- CIImage
-  colorSpace 

Instance Property

# colorSpace

The color space of the image.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.4+tvOS 9.0+visionOS 1.0+

``` source
var colorSpace: CGColorSpace? { get }
```

## Discussion

This property’s value is `nil` if the image’s color space cannot be determined.

## See Also

### Getting Image Information

var definition: CIFilterShape

Returns a filter shape object that represents the domain of definition of the image.

var extent: CGRect

A rectangle that specifies the extent of the image.

var properties: [String : Any]

A dictionary containing metadata about the image.

var url: URL?

The URL from which the image was loaded.

func orientationTransform(forExifOrientation: Int32) -> CGAffineTransform

Returns the transformation needed to reorient the image to the specified orientation.

