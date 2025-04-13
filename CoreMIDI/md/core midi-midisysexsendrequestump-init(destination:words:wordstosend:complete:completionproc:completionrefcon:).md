

- Core MIDI
- MIDISysexSendRequestUMP
-  init(destination:words:wordsToSend:complete:completionProc:completionRefCon:) 

Initializer

# init(destination:words:wordsToSend:complete:completionProc:completionRefCon:)

Creates a new single universal MIDI packet (UMP) system-exclusive (SysEx) event request.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
init(
    destination: MIDIEndpointRef,
    words: UnsafeMutablePointer,
    wordsToSend: UInt32,
    complete: DarwinBoolean,
    completionProc: MIDICompletionProcUMP,
    completionRefCon: UnsafeMutableRawPointer?
)
```

## Parameters 

`destination`  

The endpoint to send the event to.

`words`  

Initially, a pointer to the UMP SysEx event to send. The system advances this pointer as it sends the data.

`wordsToSend`  

Initially, a counter of the number of words to send. The system decrements this counter as it sends the data.

`complete`  

A Boolean value that indicates whether the transmission is complete. You can set this value to `true` to abort transmission. The system sets it to `true` after it transmits all the bytes.

`completionProc`  

A function that the system calls after it sends all data for the request, or after the client sets `complete` to `true`.

`completionRefCon`  

Data to pass to the `completionProc`.

