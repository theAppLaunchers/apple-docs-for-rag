

- Core MIDI
-  kMIDIPropertyAdvanceScheduleTimeMuSec 

Global Variable

# kMIDIPropertyAdvanceScheduleTimeMuSec

The recommended number of microseconds in advance that clients should schedule output.

iOS 4.2+iPadOS 4.2+Mac Catalyst 13.1+macOS 10.0+visionOS 1.0+

``` source
let kMIDIPropertyAdvanceScheduleTimeMuSec: CFString
```

## Discussion

Only the driver that owns the object may set this property.

If this property value is nonzero, clients should treat the value as a minimum. For devices with a nonzero advance schedule time, drivers receive outgoing messages to the device at the time the client sends them using MIDISend(_:_:_:). The driver is responsible for scheduling events to play at the right times, according to their timestamps.

You can also set this property on any virtual destinations you create. When clients send messages to a virtual destination with an advance schedule time of 0, the destination receives the messages at the scheduled delivery time. If a virtual destination has a nonzero advance schedule time, it receives timestamped messages as soon as they’re sent, and must do its own internal scheduling of events it receives.

## See Also

### Timing

let kMIDIPropertyTransmitsMTC: CFString

A Boolean value that indicates whether the device or entity transmits MIDI Time Code messages.

let kMIDIPropertyReceivesMTC: CFString

A Boolean value that indicates whether the device or entity responds to MIDI Time Code messages.

let kMIDIPropertyTransmitsClock: CFString

A Boolean value that indicates whether the device or entity transmits MIDI beat clock messages.

let kMIDIPropertyReceivesClock: CFString

A Boolean value that indicates whether the device or entity responds to MIDI beat clock messages.

