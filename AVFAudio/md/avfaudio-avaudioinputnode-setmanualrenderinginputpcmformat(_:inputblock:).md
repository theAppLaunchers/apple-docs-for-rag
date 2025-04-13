

- AVFAudio
- AVAudioInputNode
-  setManualRenderingInputPCMFormat(\_:inputBlock:) 

Instance Method

# setManualRenderingInputPCMFormat(\_:inputBlock:)

Supplies the data through the input node to the engine while operating in the manual rendering mode.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.13+tvOS 11.0+visionOS 1.0+watchOS 4.0+

``` source
func setManualRenderingInputPCMFormat(
    _ format: AVAudioFormat,
    inputBlock block: @escaping AVAudioIONodeInputBlock
) -> Bool
```

## Parameters 

`format`  

The format of the PCM audio data the block supplies to the engine.

`block`  

The block the engine calls on the input node to get the audio to send to the output when operating in the manual rendering mode. For more information, see AVAudioIONodeInputBlock.

## Discussion

The block must be non-`nil` when using an input node while the engine is operating in manual rendering mode. If you switch the engine to render to and from an audio device, it invalidates any previous block.

## See Also

### Manually Giving Data to an Audio Engine

typealias AVAudioIONodeInputBlock

The type that represents a block to render operation calls to get input data when in manual rendering mode.

