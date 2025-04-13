

- Video Toolbox
-  kVTCompressionPropertyKey_StereoCameraBaseline 

Global Variable

# kVTCompressionPropertyKey_StereoCameraBaseline

A value that specifies the distance between centers of the lenses of the camera system.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+visionOS 1.0+

``` source
let kVTCompressionPropertyKey_StereoCameraBaseline: CFString
```

## Discussion

This property sets a value for the kCMFormatDescriptionExtension_StereoCameraBaseline format description on the output samples. The value is an unsigned 32-bit integer in micrometers, or thousandths of a millimeter (for example 63123 micrometers is 63.123 millimeters).

This property is optional. Only specify a value if you know the specific distance.

## See Also

### Video Extended Usage (VEXU) Signaling

let kVTCompressionPropertyKey_HeroEye: CFString

A value that indicates which eye is the primary eye when rendering in 2D.

let kVTCompressionPropertyKey_HorizontalDisparityAdjustment: CFString

A value that indicates a relative shift of the left and right images, which changes the zero parallax plane.

let kVTCompressionPropertyKey_ProjectionKind: CFString

A value that indicates the projection kind.

let kVTCompressionPropertyKey_ViewPackingKind: CFString

A value that indicates the view packing kind.

