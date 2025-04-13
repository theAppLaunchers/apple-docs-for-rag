

- AVFAudio
- AVAudioEngine
-  connect(\_:to:fromBus:toBus:format:) 

Instance Method

# connect(\_:to:fromBus:toBus:format:)

Establishes a connection between two nodes, specifying the input and output busses.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func connect(
    _ node1: AVAudioNode,
    to node2: AVAudioNode,
    fromBus bus1: AVAudioNodeBus,
    toBus bus2: AVAudioNodeBus,
    format: AVAudioFormat?
)
```

## Parameters 

`node1`  

The source audio node.

`node2`  

The destination audio node.

`bus1`  

The output bus of the source audio node.

`bus2`  

The input bus of the destination audio node.

`format`  

If not `NULL`, the engine uses this value for the format of the source audio node’s output bus. In all cases, the engine matches the format of the destination audio node’s input bus to the source audio node’s output bus.

## Discussion

Audio nodes have input and output busses (AVAudioNodeBus). Use this method to establish connections between audio nodes. Connections are always one-to-one, never one-to-many or many-to-one.

Note

This breaks any preexisting connections that involve the source’s output bus or the destination’s input bus.

## See Also

### Connecting and Disconnecting Audio Nodes

func connect(AVAudioNode, to: AVAudioNode, format: AVAudioFormat?)

Establishes a connection between two nodes.

func disconnectNodeInput(AVAudioNode)

Removes all input connections of the node.

func disconnectNodeInput(AVAudioNode, bus: AVAudioNodeBus)

Removes the input connection of a node on the specified bus.

func disconnectNodeOutput(AVAudioNode)

Removes all output connections of a node.

func disconnectNodeOutput(AVAudioNode, bus: AVAudioNodeBus)

Removes the output connection of a node on the specified bus.

