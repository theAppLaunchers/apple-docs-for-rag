

- AVFoundation
- AVPlayerItem
-  seekingWaitsForVideoCompositionRendering 

Instance Property

# seekingWaitsForVideoCompositionRendering

A Boolean value that indicates whether the item’s timing follows the displayed video frame when seeking with a video composition.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.0+visionOS 1.0+

``` source
nonisolated
var seekingWaitsForVideoCompositionRendering: Bool { get set }
```

## Discussion

By default, item timing is updated as quickly as possible during seeking. Specifically, the item does not wait for new frames to be rendered when seeking during normal playback. In most situations, the latency between the completion of a seek operation and the display of a video frame at the new time is negligible. However, when video compositions are in use, the processing of video may introduce noticeable latency. Setting the value of this property to true causes the item’s timing to be updated only after the corresponding video frame has been displayed. For example, this allows an AVSynchronizedLayer object associated with the item to remain in sync with the displayed video.

This property has no effect on items whose videoComposition property is `nil`.

## See Also

### Configuring Video Compositing

var videoComposition: AVVideoComposition?

The video composition settings to be applied during playback.

var customVideoCompositor: (any AVVideoCompositing)?

The custom video compositor.

