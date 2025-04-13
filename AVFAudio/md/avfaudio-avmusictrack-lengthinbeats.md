

- AVFAudio
- AVMusicTrack
-  lengthInBeats 

Instance Property

# lengthInBeats

The total duration of the track, in beats.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
var lengthInBeats: AVMusicTimeStamp { get set }
```

## Discussion

This property returns the beat of the last event in the track, plus any additional time that’s necessary to fade out the ending notes, or to round a loop point to a musical bar.

If the user doesn’t set this value, the track length always adjusts to the end of the last active event in a track, and adjusts dynamically as the user adds or removes events.

This property returns the maximum of the user-set track length or the calculated length.

## See Also

### Configuring the Track Duration

var lengthInSeconds: TimeInterval

The total duration of the track, in seconds.

