

- Core MIDI
-  MIDIEventPacketSysexBytesForGroup(\_:\_:\_:) 

Function

# MIDIEventPacketSysexBytesForGroup(\_:\_:\_:)

Gets MIDI 1.0 system-exclusive (SysEx) bytes on the indicated group.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+visionOS 1.0+

``` source
func MIDIEventPacketSysexBytesForGroup(
    _ pkt: UnsafePointer,
    _ groupIndex: UInt8,
    _ outData: UnsafeMutablePointer?>
) -> OSStatus
```

## Parameters 

`pkt`  

A MIDIEventPacket that contains universal MIDI packet (UMP) SysEx data.

`groupIndex`  

The target group index, from `0` to `15`.

`outData`  

When successful, a reference byte stream of extracted SysEx data.

## Return Value

An `OSStatus` result code.

## See Also

### Configuring and inspecting a request

var destination: MIDIEndpointRef

The endpoint to send the event to.

var words: UnsafeMutablePointer&lt;UInt32>

A pointer to the event to send, which the system advances as it sends the data.

var wordsToSend: UInt32

A counter of the number of words to send.

var complete: DarwinBoolean

A Boolean value that indicates whether the transmission is complete.

typealias MIDICompletionProcUMP

A function the system calls after it completely sends a UMP system-exclusive (SysEx) or SysEx 8-bit event.

var completionProc: MIDICompletionProcUMP

A function that the system calls after it sends all data for the request, or after the client marks the request as complete.

var completionRefCon: UnsafeMutableRawPointer?

Data to pass to the completion function.

