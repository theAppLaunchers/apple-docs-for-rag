

- Video Toolbox
-  kVTCompressionPropertyKey_CleanAperture 

Global Variable

# kVTCompressionPropertyKey_CleanAperture

The clean aperture for encoded frames.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.8+tvOS 10.2+visionOS 1.0+

``` source
let kVTCompressionPropertyKey_CleanAperture: CFString
```

## Discussion

If a video encoder enforces specific clean apertures, this property is read-only (VTSessionSetProperty(_:key:value:) will return kVTPropertyReadOnlyErr). The clean aperture will be set on the format description for output samples, and may affect source frame scaling. NULL is a valid value for this property, meaning that the clean aperture is the full width and height.

## See Also

### Clean Aperture and Pixel Aspect Ratio

let kVTCompressionPropertyKey_AspectRatio16x9: CFString

A Boolean value indicating whether the DV video stream should have the 16x9 flag set.

let kVTCompressionPropertyKey_FieldCount: CFString

The field count indicating whether the frames should be encoded progressive (1) or interlaced (2).

let kVTCompressionPropertyKey_FieldDetail: CFString

Field ordering for encoded interlaced frames.

let kVTCompressionPropertyKey_PixelAspectRatio: CFString

The pixel aspect ratio for encoded frames.

let kVTCompressionPropertyKey_ProgressiveScan: CFString

A Boolean value indicating whether the DV video stream should have the progressive flag set.

