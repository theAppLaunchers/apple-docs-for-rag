

- ARKit
- ImageAnchor
-  estimatedScaleFactor 

Instance Property

# estimatedScaleFactor

The estimated scale factor between the tracked image’s physical size and the reference image’s size.

visionOS 1.0+

``` source
var estimatedScaleFactor: Float { get }
```

## Discussion

The scale factor is between the tracked image’s size and the physicalSize property on the reference image you supply when you create an image tracking provider. For example, if you supply a reference image and the version that appears in front of someone is three times larger, this property is `3.0`.

## See Also

### Getting image information

var originFromAnchorTransform: simd_float4x4

The location and orientation of the image in world space.

var referenceImage: ReferenceImage

The reference image that this image anchor tracks.

var isTracked: Bool

A Boolean value that indicates whether ARKit is currently tracking this image.

var description: String

A textual representation of this anchor.

var id: UUID

The unique identifier of this anchor.

