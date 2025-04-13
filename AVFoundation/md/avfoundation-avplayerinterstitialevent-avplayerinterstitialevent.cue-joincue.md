

- AVFoundation
- AVPlayerInterstitialEvent
- AVPlayerInterstitialEvent.Cue
-  joinCue 

Type Property

# joinCue

A cue that indicates that playback occurs before starting primary playback, regardless of initial primary playback position.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
static let joinCue: AVPlayerInterstitialEvent.Cue
```

## See Also

### Cues

static let noCue: AVPlayerInterstitialEvent.Cue

A cue that indicates that playback starts at the interstitial event time or date.

static let leaveCue: AVPlayerInterstitialEvent.Cue

A cue that indicates event playback occurs after primary playback ends without error, either at the end of the primary asset or at the client-specified forward playback end time.

