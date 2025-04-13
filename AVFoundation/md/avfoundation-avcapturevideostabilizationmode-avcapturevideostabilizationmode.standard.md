

- AVFoundation
- AVCaptureVideoStabilizationMode
-  AVCaptureVideoStabilizationMode.standard 

Case

# AVCaptureVideoStabilizationMode.standard

A mode that uses the standard algorithm.

iOS 8.0+iPadOS 8.0+Mac Catalyst 14.0+tvOS 17.0+

``` source
case standard
```

## Discussion

Standard video stabilization has a reduced field of view. Enabling video stabilization may introduce additional latency into the video capture pipeline.

## See Also

### Stabilization Modes

case off

A mode that doesn’t stabilize video capture.

case cinematic

A mode that uses the cinematic stabilization algorithm.

case cinematicExtended

A mode that uses the extended cinematic stabilization algorithm.

case previewOptimized

A mode that uses the preview optimized stabilization algorithm.

case cinematicExtendedEnhanced

A mode that stabilizes video using the enhanced extended cinematic stabilization algorithm.

case auto

A mode that indicates the system chooses the most appropriate video stabilization mode for the device and format.

