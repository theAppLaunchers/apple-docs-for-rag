

- AVFoundation
- AVMutableVideoComposition
-  perFrameHDRDisplayMetadataPolicy 

Instance Property

# perFrameHDRDisplayMetadataPolicy

Configures the policy for display of HDR display metadata on the rendered frame.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+visionOS 1.0+

``` source
var perFrameHDRDisplayMetadataPolicy: AVVideoComposition.PerFrameHDRDisplayMetadataPolicy { get set }
```

## Discussion

Allows the system to identify situations where it can generate HDR metadata and attach it to the rendered video frame.

The default value is propagate, which indicates the system propagates any HDR metadata attached to the composed frame to the rendered video frames.

## See Also

### Configuring HDR Metadata

struct PerFrameHDRDisplayMetadataPolicy

A type that defines the policy for handling of per frame HDR metadata.

