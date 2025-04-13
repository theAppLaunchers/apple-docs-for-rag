

- MusicKit
- MusicPlayer
- MusicPlayer.State
-  playbackRate 

Instance Property

# playbackRate

The current playback rate for the player.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 14.0+tvOS 15.0+visionOS 1.0+

``` source
var playbackRate: Float { get set }
```

## Discussion

This value represents a multiplier for the default playback rate of the current entry. A value of `0.0` indicates that the entry isn’t playing, and a value of `1.0` indicates that it’s playing at normal speed. Positive values indicate forward playback, and negative values indicate reverse playback.

Setting the value of this property changes the playback rate accordingly.

