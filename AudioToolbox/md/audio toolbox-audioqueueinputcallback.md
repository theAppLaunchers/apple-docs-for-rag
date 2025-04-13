

- Audio Toolbox
-  AudioQueueInputCallback 

Type Alias

# AudioQueueInputCallback

Called by the system when a recording audio queue has finished filling an audio queue buffer.

iOSiPadOSMac CatalystmacOStvOSvisionOS

``` source
typealias AudioQueueInputCallback = (UnsafeMutableRawPointer?, AudioQueueRef, AudioQueueBufferRef, UnsafePointer, UInt32, UnsafePointer?) -> Void
```

## Parameters 

`inUserData`  

The custom data you’ve specified in the `inUserData` parameter of the AudioQueueNewInput(_:_:_:_:_:_:_:) function. Typically, this includes format and state information for the audio queue.

`inAQ`  

The recording audio queue that invoked the callback.

`inBuffer`  

An audio queue buffer, newly filled by the recording audio queue, containing the new audio data your callback needs to write.

`inStartTime`  

The sample time for the start of the audio queue buffer. This parameter is not used in basic recording.

`inNumberPacketDescriptions`  

The number of packets of audio data sent to the callback in the `inBuffer` parameter. When recording in a constant bit rate (CBR) format, the audio queue sets this parameter to `NULL`.

`inPacketDescs`  

For compressed formats that require packet descriptions, the set of packet descriptions produced by the encoder for audio data in the `inBuffer` parameter. When recording in a CBR format, the audio queue sets this parameter to `NULL`.

## Discussion

If you name your callback function `MyAudioQueueInputCallback`, you would declare it like this:

### Discussion

You specify a recording audio queue callback when calling the AudioQueueNewInput(_:_:_:_:_:_:_:) function. The callback is invoked each time its recording audio queue has filled an audio queue buffer with fresh audio data. Typically, your callback writes the data to a file or other buffer, and then reenqueues the audio queue buffer to receive more data.

## See Also

### Callbacks

typealias AudioQueueOutputCallback

Called by the system when an audio queue buffer is available for reuse.

typealias AudioQueuePropertyListenerProc

Called by the system when a specified audio queue property changes value.

