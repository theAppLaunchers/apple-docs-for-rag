

- RealityKit
- ActionAnimation
-  repeatMode 

Instance Property

# repeatMode

An option that determines how the animation repeats.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
var repeatMode: AnimationRepeatMode { get set }
```

## Discussion

If you call `AnimationAction/trimmed(start:end:duration:)` with a `start` or `end` that lies outside of the timeline defined by `AnimationAction/duration`, the animation fills the additional playback by applying this property.

