

- AVFoundation
- AVCaptureDevice
- AVCaptureDevice.Format
-  isHighestPhotoQualitySupported 

Instance Property

# isHighestPhotoQualitySupported

A Boolean value that indicates whether this format supports the highest photo quality that the platform delivers.

iOS 13.0+iPadOS 13.0+Mac Catalyst 14.0+tvOS 17.0+

``` source
var isHighestPhotoQualitySupported: Bool { get }
```

## Discussion

The simplest way to capture the highest quality photos is to set photo as your session’s preset. If you’re instead manually setting the capture device’s activeFormat value, select the format whose isHighestPhotoQualitySupported property is true.

## See Also

### Determining Photo Quality

var supportedMaxPhotoDimensions: [CMVideoDimensions]

The maximum photo dimension this format supports.

var isHighPhotoQualitySupported: Bool

A Boolean value that indicates whether this format supports high-quality capture with the current quality prioritization setting.

