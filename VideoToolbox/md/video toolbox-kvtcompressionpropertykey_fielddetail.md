

- Video Toolbox
-  kVTCompressionPropertyKey_FieldDetail 

Global Variable

# kVTCompressionPropertyKey_FieldDetail

Field ordering for encoded interlaced frames.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.8+tvOS 10.2+visionOS 1.0+

``` source
let kVTCompressionPropertyKey_FieldDetail: CFString
```

## Discussion

If a video encoder enforces specific field ordering, this property will be read-only (VTSessionSetProperty(_:key:value:) returns kVTPropertyReadOnlyErr). The field detail is set on the format description for output samples, and may affect source frame scaling. `NULL` is a valid value for this property.

## See Also

### Clean Aperture and Pixel Aspect Ratio

let kVTCompressionPropertyKey_AspectRatio16x9: CFString

A Boolean value indicating whether the DV video stream should have the 16x9 flag set.

let kVTCompressionPropertyKey_CleanAperture: CFString

The clean aperture for encoded frames.

let kVTCompressionPropertyKey_FieldCount: CFString

The field count indicating whether the frames should be encoded progressive (1) or interlaced (2).

let kVTCompressionPropertyKey_PixelAspectRatio: CFString

The pixel aspect ratio for encoded frames.

let kVTCompressionPropertyKey_ProgressiveScan: CFString

A Boolean value indicating whether the DV video stream should have the progressive flag set.

