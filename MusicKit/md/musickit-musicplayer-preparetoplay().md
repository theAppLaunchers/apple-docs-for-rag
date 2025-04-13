

- MusicKit
- MusicPlayer
-  prepareToPlay() 

Instance Method

# prepareToPlay()

Prepares the current queue for playback, interrupting any active (nonmixable) audio sessions.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 14.0+tvOS 15.0+visionOS 1.0+

``` source
func prepareToPlay() async throws
```

## Discussion

Call this function to ensure that the player buffers the starting entry in the queue and that the entry is ready to play.

