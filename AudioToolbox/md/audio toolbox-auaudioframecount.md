

- Audio Toolbox
-  AUAudioFrameCount 

Type Alias

# AUAudioFrameCount

A number of audio sample frames.

iOSiPadOSMac CatalystmacOStvOSvisionOS

``` source
typealias AUAudioFrameCount = UInt32
```

## Discussion

This alias is type `uint32_t` for impedance-matching with the pervasive use of `UInt32` in the Audio Toolbox framework and the C Audio Unit framework APIs, as well as the AVAudioFrameCount data type.

## See Also

### Audio Unit Types

struct ScheduledAudioFileRegion

struct ScheduledAudioSlice

typealias ScheduledAudioFileRegionCompletionProc

typealias ScheduledAudioSliceCompletionProc

typealias MIDIChannelNumber

MIDI Channel, 0~15 (channels 1 through 16, respectively).

typealias AUAudioObjectID

typealias AUMIDICIProfileChangedBlock

typealias AUAudioChannelCount

A number of audio channels.

typealias AUAudioUnitStatus

A result code returned from an audio unit’s render function.

typealias AUEventListenerProc

typealias AUEventListenerRef

typealias AUEventSampleTime

Expresses time as a sample count.

typealias AUImplementorValueObserver

A block called to notify the audio unit implementation of changes to a parameter value.

typealias AUImplementorValueProvider

A block called to fetch a parameter’s current value from the audio unit implementation.

typealias AUInputHandler

A block to notify the host of an I/O unit that an input is available.

