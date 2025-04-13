

- Audio Toolbox
-  AudioQueuePropertyID 

Type Alias

# AudioQueuePropertyID

Identifiers for audio queue properties.

iOSiPadOSMac CatalystmacOStvOSvisionOS

``` source
typealias AudioQueuePropertyID = UInt32
```

## Discussion

To receive a notification that a specific audio queue property has changed:

1.  Define a property listener callback, referencing the desired audio queue property ID. Base the callback on the AudioQueuePropertyListenerProc callback function declaration.

2.  Assign the callback to an audio queue using the AudioQueueAddPropertyListener(_:_:_:_:) function.

3.  When you get a property-changed notification, call the AudioQueueGetProperty(_:_:_:_:) function to get the current value of the property.

## Topics

### Constants

var kAudioQueueProperty_IsRunning: AudioQueuePropertyID

Value is a read-only `UInt32` value indicating whether or not the audio queue is running. A nonzero value means running; `0` means stopped. A notification is sent when the associated audio queue starts or stops, which may occur sometime after the AudioQueueStart(_:_:) or AudioQueueStop(_:_:) function is called.

var kAudioQueueDeviceProperty_SampleRate: AudioQueuePropertyID

Value is a read-only `Float64` value representing the sampling rate of the audio hardware device associated with an audio queue.

var kAudioQueueDeviceProperty_NumberChannels: AudioQueuePropertyID

Value is a read-only `UInt32` value representing the number of channels in the audio hardware device associated with an audio queue.

var kAudioQueueProperty_CurrentDevice: AudioQueuePropertyID

The unique identifier (UID) of the audio hardware device.

var kAudioQueueProperty_MagicCookie: AudioQueuePropertyID

Value is a read/write void pointer to a block of memory, which you set up, containing an audio format magic cookie. If the audio format you are playing or recording to requires a magic cookie, you must set a value for this property before enqueuing any buffers.

var kAudioQueueProperty_MaximumOutputPacketSize: AudioQueuePropertyID

Value is a read-only`UInt32` value that is the size, in bytes, of the largest single packet of data in the output format. Primarily useful when encoding VBR compressed data.

var kAudioQueueProperty_StreamDescription: AudioQueuePropertyID

An audio queue’s data format.

var kAudioQueueProperty_ChannelLayout: AudioQueuePropertyID

Describes an audio queue channel layout.

var kAudioQueueProperty_EnableLevelMetering: AudioQueuePropertyID

Value is a read/write `UInt32` value that indicates whether audio level metering is enabled for an audio queue. `0` = metering off, `1` = metering on.

var kAudioQueueProperty_CurrentLevelMeter: AudioQueuePropertyID

A read-only array of level meter status structures.

var kAudioQueueProperty_CurrentLevelMeterDB: AudioQueuePropertyID

Value is a read-only array of AudioQueueLevelMeterState structures, one array element per audio channel. The member values in the structure are in decibels.

var kAudioQueueProperty_DecodeBufferSizeFrames: AudioQueuePropertyID

Value is a read/write `UInt32` value that is the size of the buffer into which a playback (output) audio queue decodes buffers. A larger buffer provides more reliability and better long-term performance at the expense of memory and decreased responsiveness in some situations.

var kAudioQueueProperty_ConverterError: AudioQueuePropertyID

Value is a read-only `UInt32` value that indicates the most recent error (if any) encountered by the audio queue’s internal encoding/decoding process.

## See Also

### Constants

Audio Queue Parameters

Identifiers for audio queue parameters.

Hardware Codec Policy Keys

Indicates how an audio queue should choose between hardware and software implementations of a codec.

