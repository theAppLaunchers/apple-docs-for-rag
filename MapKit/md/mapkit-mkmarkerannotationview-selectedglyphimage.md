

- MapKit
- MKMarkerAnnotationView
-  selectedGlyphImage 

Instance Property

# selectedGlyphImage

An image to display when the user selects the marker.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 11.0+tvOS 11.0+visionOS 1.0+

**macOS**

``` source
@NSCopying @MainActor
var selectedGlyphImage: NSImage? { get set }
```

**iOS, iPadOS, Mac Catalyst, tvOS, visionOS**

``` source
@NSCopying @MainActor
var selectedGlyphImage: UIImage? { get set }
```

## Discussion

MapKit displays the glyph image when the marker is in the selected state. If you specify an image for this property, you should also specify an image in the glyphImage property.

Create glyph images as template images so that MapKit can apply the glyph tint color to the image. Set the size of this image to 40 by 40 points on iOS and 60 by 40 points on tvOS. MapKit scales images that are larger or smaller than those sizes.

## See Also

### Setting the Marker Content

var glyphText: String?

The text to display in the marker balloon.

var glyphImage: UIImage?

An image to display in the marker balloon.

var glyphTintColor: UIColor?

The color to apply to the glyph text or image.

