

- PHASE
-  PHASEPullStreamRenderHandler 

Type Alias

# PHASEPullStreamRenderHandler

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+

``` source
typealias PHASEPullStreamRenderHandler = (UnsafeMutablePointer, UnsafePointer, AVAudioFrameCount, UnsafeMutablePointer) -> OSStatus
```

## Parameters 

`timestamp`  

The HAL time at which the audio data will be rendered. If there is a sample rate conversion or time compression/expansion downstream, the sample time will not be valid.

`frameCount`  

The number of sample frames of audio data requested.

`outputData`  

The output data.

## Return Value

An OSStatus result code. If an error is returned, the audio data should be assumed to be invalid.

## Discussion

```
The client may use this flag to indicate that the buffer it vends contains only silence.
The receiver of the buffer can then use the flag as a hint as to whether the buffer needs
to be processed or not.
Note that because the flag is only a hint, when setting the silence flag, the originator of
a buffer must also ensure that it contains silence (zeroes).
```

```
The caller must supply valid buffers in outputData's mBuffers' mData and mDataByteSize.
mDataByteSize must be consistent with frameCount. This block may provide output in those
specified buffers, or it may replace the mData pointers with pointers to memory which it
owns and guarantees will remain valid until the next render cycle.
```

