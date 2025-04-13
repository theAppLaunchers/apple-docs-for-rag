

- AVFAudio
- AVAudioEngine
-  enableManualRenderingMode(\_:format:maximumFrameCount:) 

Instance Method

# enableManualRenderingMode(\_:format:maximumFrameCount:)

Sets the engine to operate in manual rendering mode with the render format and maximum frame count you specify.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.13+tvOS 11.0+visionOS 1.0+watchOS 4.0+

``` source
func enableManualRenderingMode(
    _ mode: AVAudioEngineManualRenderingMode,
    format pcmFormat: AVAudioFormat,
    maximumFrameCount: AVAudioFrameCount
) throws
```

## Parameters 

`mode`  

The manual rendering mode to use.

`pcmFormat`  

The format of the output PCM audio data from the engine.

`maximumFrameCount`  

The maximum number of PCM sample frames the engine produces in a single render call.

## Discussion

Use this method to configure the engine to render in response to requests from the client. You must stop the engine before calling this method. The render format must be a PCM format and match the format of the rendering buffer.

The source nodes can supply the input data in manual rendering mode. For more information, see AVAudioPlayerNode and AVAudioInputNode.

## See Also

### Manually Rendering an Audio Engine

func disableManualRenderingMode()

Sets the engine to render to or from an audio device.

func renderOffline(AVAudioFrameCount, to: AVAudioPCMBuffer) throws -> AVAudioEngineManualRenderingStatus

Makes a render call to the engine operating in the offline manual rendering mode.

