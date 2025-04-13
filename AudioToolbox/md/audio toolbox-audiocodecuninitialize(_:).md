

- Audio Toolbox
-  AudioCodecUninitialize(\_:) 

Function

# AudioCodecUninitialize(\_:)

Moves the codec from the initialized state back to the uninitialized state.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.2+tvOS 9.0+visionOS 1.0+

``` source
func AudioCodecUninitialize(_ inCodec: AudioCodec) -> OSStatus
```

## Parameters 

`inCodec`  

An audio codec object. Because an audio codec object is a Component Manger component instance, you can use the Component Manager (for example, the functions FindNextComponent and OpenAComponent) to obtain an audio codec object.

## Return Value

Returns `NoErr` if successful, otherwise, a result code. See `Result Codes` for a list of possible values.

## Discussion

This function returns the codec to the uninitialized state. The codec may then be configured freely. This function does not flush the input buffer or clear input and output formats, magic cookie data, and other state variables. It is not necessary to call this function before closing the codec.

## See Also

### Related Documentation

func AudioCodecSetProperty(AudioCodec, AudioCodecPropertyID, UInt32, UnsafeRawPointer) -> OSStatus

Sets the value of a codec property.

### Initializing an Audio Codec

func AudioCodecInitialize(AudioCodec, UnsafePointer&lt;AudioStreamBasicDescription>?, UnsafePointer&lt;AudioStreamBasicDescription>?, UnsafeRawPointer?, UInt32) -> OSStatus

Sets up the specified codec to perform a data format translation.

func AudioCodecReset(AudioCodec) -> OSStatus

Flushes all the audio data in the codec and clears the input buffer.

