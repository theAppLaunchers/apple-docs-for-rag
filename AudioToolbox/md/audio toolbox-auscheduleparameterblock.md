

- Audio Toolbox
-  AUScheduleParameterBlock 

Type Alias

# AUScheduleParameterBlock

A block to schedule parameter changes.

iOSiPadOSMac CatalystmacOStvOSvisionOS

``` source
typealias AUScheduleParameterBlock = (AUEventSampleTime, AUAudioFrameCount, AUParameterAddress, AUValue) -> Void
```

## Discussion

Check the parameter’s flags to determine whether the parameter is rampable.

The block takes the following parameters:

eventSampleTime  
The sample time at which the parameter is to begin changing. When scheduling parameters during the render cycle, this time can be set to the `AUEventSampleTimeImmediate` value plus an optional buffer offset, in which case the event is scheduled at that position in the current render cycle.

rampDurationSampleFrames  
The number of sample frames over which the parameter’s return value is to ramp, or `0` if the parameter change should take effect immediately.

parameterAddress  
The parameter’s address.

value  
The parameter’s new value if the ramp duration is `0`; otherwise, the value at the end of the scheduled ramp.

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

typealias AUAudioFrameCount

A number of audio sample frames.

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

