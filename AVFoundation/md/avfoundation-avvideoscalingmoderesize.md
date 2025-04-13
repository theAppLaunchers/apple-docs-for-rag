

- AVFoundation
-  AVVideoScalingModeResize 

Global Variable

# AVVideoScalingModeResize

The string identifier for resizing a video to fit the surrounding view’s dimensions.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+

``` source
let AVVideoScalingModeResize: String
```

## Discussion

This mode crops the video to remove the edge processing region and scales the remainder to the destination area. It doesn’t preserve the aspect ratio.

## See Also

### Scaling mode

let AVVideoScalingModeFit: String

The string identifier for scaling a video to fit the surrounding view’s dimensions.

let AVVideoScalingModeKey: String

A key to retrieve the video scaling mode from a dictionary.

let AVVideoScalingModeResizeAspect: String

The string identifier for resizing a video to its surrounding view’s shorter dimension while preserving its aspect ratio.

let AVVideoScalingModeResizeAspectFill: String

The string identifier for resizing a video to fit the surrounding view’s longer dimension while preserving aspect ratio.

