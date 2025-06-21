*   [Video Toolbox](/documentation/videotoolbox)
*   [Frame processing](/documentation/videotoolbox/frame-processing)
*   Enhancing your app with machine learning-based video effects

Sample Code

# Enhancing your app with machine learning-based video effects

Add powerful effects to your videos using the VideoToolbox VTFrameProcessor API.

[Download](https://docs-assets.developer.apple.com/published/e4b9ff471ffd/EnhancingYourAppWithMachineLearningBasedVideoEffects.zip)

macOS 15.4+Xcode 16.4+

## [Overview](/documentation/VideoToolbox/enhancing-your-app-with-machine-learning-based-video-effects#Overview)

Using this sample app, you can learn how to enhance your videos using one of several video effects.

Note

This sample code project is associated with WWDC25 session 300: [Enhance your app with machine learning-based video effects](https://developer.apple.com/videos/play/wwdc2025/300).

## [See Also](/documentation/VideoToolbox/enhancing-your-app-with-machine-learning-based-video-effects#see-also)

### [Frame processor](/documentation/VideoToolbox/enhancing-your-app-with-machine-learning-based-video-effects#Frame-processor)

```swift
```swift
```swift
```swift
class VTFrameProcessor
```
```

A class that creates a new frame processor for the configured video effect.
```
```swift
```swift
```swift
class VTFrameProcessorFrame
```
```

An object that wraps video frames to send to the processor, as source, reference, or output frames.
```
```swift
```swift
```swift
protocol VTFrameProcessorConfiguration
```
```

A protocol that describes the configuration of a processor to use during a video processing session.
```
```swift
```swift
```swift
protocol VTFrameProcessorParameters
```
```

The base protocol for input and output processing parameters for a frame processor implementation.
```
```