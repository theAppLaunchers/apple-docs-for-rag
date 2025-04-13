

- RealityKit
- VideoMaterial
-  avPlayer 

Instance Property

# avPlayer

The material’s video playback controller.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+visionOS

``` source
@MainActor @preconcurrency
var avPlayer: AVPlayer? { get set }
```

## Discussion

Use this property to control animation playback for a video texture. This property allows you to play or pause the movie, *seek to* (in other words, skip to) a specific part of the movie, or to change the movie’s playback rate. The following code demonstrates pausing the texture’s video and restarting it from the beginning of the movie file:

```
myMaterial.avPlayer.pause()
myMaterial.avPlayer.seek(to: .zero)
myMaterial.avPlayer.play()
```

## See Also

### Controlling playback

var controller: VideoPlaybackController

An object that configures framework-specific video options.

