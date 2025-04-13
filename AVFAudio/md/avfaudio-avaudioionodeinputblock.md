

- AVFAudio
-  AVAudioIONodeInputBlock 

Type Alias

# AVAudioIONodeInputBlock

The type that represents a block to render operation calls to get input data when in manual rendering mode.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.13+tvOS 11.0+visionOS 1.0+watchOS 4.0+

``` source
typealias AVAudioIONodeInputBlock = (AVAudioFrameCount) -> UnsafePointer?
```

## Parameters 

`inNumberOfFrames`  

The number of frames the system needs to complete the request.

## Return Value

An AudioBufferList that contains the data to render, or `nil` if no data is available.

## Discussion

Don’t clear or refill the data in the return value until the framework calls the input block again or the rendering finishes. The format of the buffer list must match the format you specify when registering the block.

## See Also

### Manually Giving Data to an Audio Engine

func setManualRenderingInputPCMFormat(AVAudioFormat, inputBlock: AVAudioIONodeInputBlock) -> Bool

Supplies the data through the input node to the engine while operating in the manual rendering mode.

