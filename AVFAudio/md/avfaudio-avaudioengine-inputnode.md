

- AVFAudio
- AVAudioEngine
-  inputNode 

Instance Property

# inputNode

The audio engine’s singleton input audio node.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOS 11.0+visionOS 1.0+watchOS 4.0+

``` source
var inputNode: AVAudioInputNode { get }
```

## Discussion

The framework performs audio input through an input node. The audio engine creates a singleton on demand when first accessing this variable. To receive input, connect another node from the output of the input node, or create a recording tap on it.

When the engine renders to and from an audio device, the AVAudioSession category and the availability of hardware determines whether an app performs input (for example, input hardware isn’t available in tvOS). Check the input node’s input format (specifically, the hardware format) for a nonzero sample rate and channel count to see if input is in an enabled state.

Trying to perform input through the input node when it isn’t available or in an enabled state causes the engine to throw an error (when possible) or an exception.

In manual rendering mode, the input node can synchronously supply data to the engine while it’s rendering. For more information, see setManualRenderingInputPCMFormat(_:inputBlock:).

## See Also

### Getting the Input, Output, and Main Mixer Nodes

var outputNode: AVAudioOutputNode

The audio engine’s singleton output audio node.

var mainMixerNode: AVAudioMixerNode

The audio engine’s optional singleton main mixer node.

