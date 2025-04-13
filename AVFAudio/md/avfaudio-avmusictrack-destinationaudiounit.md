

- AVFAudio
- AVMusicTrack
-  destinationAudioUnit 

Instance Property

# destinationAudioUnit

The audio unit that receives the track’s events.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
var destinationAudioUnit: AVAudioUnit? { get set }
```

## Discussion

This property and a destinationMIDIEndpoint are mutually exclusive. You must attach the audio to an audio engine to receive events. The track must be part of the AVAudioSequencer you associate with the same engine. When playing, the track sends it’s events to that AVAudioUnit. You can’t change the destination audio unit while the track’s sequence is in a playing state.

## See Also

### Configuring the Track Destinations

var destinationMIDIEndpoint: MIDIEndpointRef

The MIDI endpoint you specify as the track’s target.

