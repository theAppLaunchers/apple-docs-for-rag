

- AVFoundation
- AVCaptureConnection
-  videoScaleAndCropFactor 

Instance Property

# videoScaleAndCropFactor

The current scale and crop factor the video output uses.

iOS 5.0+iPadOS 5.0+Mac Catalyst 14.0+tvOS 17.0+

``` source
var videoScaleAndCropFactor: CGFloat { get set }
```

## Discussion

The property only applies to a video connection. You can set this property to a value in the range `[1.0,` \`\`AVCaptureConnection/videoMaxScaleAndCropFactor\`\`\`\]`. A factor of `1.0\` keeps the image at its original. Factors greater than \`1.0\` scale the image up and center-crop the image to its original dimensions.

## See Also

### Scaling a video

var videoMaxScaleAndCropFactor: CGFloat

The connection’s maximum video scale and crop factor.

