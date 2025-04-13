

- AVFoundation
- AVCapturePhoto
-  constantColorCenterWeightedMeanConfidenceLevel 

Instance Property

# constantColorCenterWeightedMeanConfidenceLevel

A score that summarizes the overall confidence level of a constant color photo.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+

``` source
var constantColorCenterWeightedMeanConfidenceLevel: Float { get }
```

## Discussion

A value of `1.0` means full confidence and `0.0` means zero confidence. The default is `0.0.`

In most use cases, such as document scanning, the system considers the central region of the photo more important than its edges. The system weights the confidence level of the central pixels more heavily than pixels on the edges of the photo.

Use constantColorConfidenceMap for more use case specific analyses of the confidence level.

## See Also

### Enabling Constant Color

var constantColorConfidenceMap: CVPixelBuffer?

A pixel buffer where each pixel value indicates how fully the system achieves the constant color effect in the corresponding region of the photo.

var isConstantColorFallbackPhoto: Bool

A Boolean value that Indicates whether this photo is a fallback photo for a constant color capture.

