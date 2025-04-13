

- AVFoundation
-  AVVideoScalingModeResizeAspect 

Global Variable

# AVVideoScalingModeResizeAspect

The string identifier for resizing a video to its surrounding view’s shorter dimension while preserving its aspect ratio.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+

``` source
let AVVideoScalingModeResizeAspect: String
```

## Discussion

This mode preserves the aspect ratio of the source and fills the remaining areas with black to fit the destination dimensions.

## See Also

### Scaling mode

let AVVideoScalingModeFit: String

The string identifier for scaling a video to fit the surrounding view’s dimensions.

let AVVideoScalingModeKey: String

A key to retrieve the video scaling mode from a dictionary.

let AVVideoScalingModeResize: String

The string identifier for resizing a video to fit the surrounding view’s dimensions.

let AVVideoScalingModeResizeAspectFill: String

The string identifier for resizing a video to fit the surrounding view’s longer dimension while preserving aspect ratio.

