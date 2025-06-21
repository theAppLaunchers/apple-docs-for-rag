*   [AVFAudio](/documentation/avfaudio)
*   AVAudioSequencer

Class

# AVAudioSequencer

An object that plays audio from a collection of MIDI events the system organizes into music tracks.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class AVAudioSequencer
```
```
```
```
```
```
```
```

## [Topics](/documentation/AVFAudio/AVAudioSequencer#topics)

### [Creating an Audio Sequencer](/documentation/AVFAudio/AVAudioSequencer#Creating-an-Audio-Sequencer)

[`init()`](/documentation/avfaudio/avaudiosequencer/init\(\))

Creates an audio sequencer object.

[`init(audioEngine: AVAudioEngine)`](/documentation/avfaudio/avaudiosequencer/init\(audioengine:\))

Creates an audio sequencer that the framework attaches to an audio engine instance.

### [Writing to a MIDI File](/documentation/AVFAudio/AVAudioSequencer#Writing-to-a-MIDI-File)

```swift
```swift
```swift
```swift
func write(to: URL, smpteResolution: Int, replaceExisting: Bool) throws
```
```

Creates and writes a MIDI file from the events in the sequence.
```
```

### [Handling Music Tracks](/documentation/AVFAudio/AVAudioSequencer#Handling-Music-Tracks)

```swift
```swift
```swift
```swift
class AVMusicTrack
```
```

A collection of music events that you can offset, set to a muted state, modify independently from other track events, and send to a specified destination.
```
```swift
```swift
```swift
func createAndAppendTrack() -> AVMusicTrack
```
```

Creates a new music track and appends it to the sequencer’s list.
```
```swift
```swift
```swift
func reverseEvents()
```
```

Reverses the order of all events in all music tracks, including the tempo track.
```
```swift
```swift
```swift
func removeTrack(AVMusicTrack) -> Bool
```
```

Removes the music track from the sequencer.
```
```swift
```swift
```swift
enum AVMusicTrackLoopCount
```
```

Options that define the number of times a track loops.
```
```

### [Handling Music Events](/documentation/AVFAudio/AVAudioSequencer#Handling-Music-Events)

```swift
```swift
```swift
```swift
class AVMusicEvent
```
```

A base class for the events you associate with a music track.
```
```swift
```swift
```swift
class AVMusicUserEvent
```
```

An object that represents a custom user message.
```
```swift
```swift
```swift
class AVParameterEvent
```
```

An object that represents a parameter event on a music track’s destination.
```
```swift
```swift
```swift
class AVAUPresetEvent
```
```

An object that represents a preset load and change on the music track’s destination audio unit.
```
```swift
```swift
```swift
class AVExtendedTempoEvent
```
```

An object that represents a tempo change to a specific beats-per-minute value.
```
```swift
```swift
```swift
class AVExtendedNoteOnEvent
```
```

An object that represents a custom extension of a MIDI note on event.
```
```

### [Handling MIDI Events](/documentation/AVFAudio/AVAudioSequencer#Handling-MIDI-Events)

```swift
```swift
```swift
```swift
class AVMIDINoteEvent
```
```

An object that represents MIDI note on or off messages.
```
```swift
```swift
```swift
class AVMIDIMetaEvent
```
```

An object that represents MIDI meta event messages.
```
```swift
```swift
```swift
class AVMIDISysexEvent
```
```

An object that represents a MIDI system exclusive message.
```
```

### [Handling MIDI Channel Events](/documentation/AVFAudio/AVAudioSequencer#Handling-MIDI-Channel-Events)

```swift
```swift
```swift
```swift
class AVMIDIChannelEvent
```
```

A base class for all MIDI messages that operate on a single MIDI channel.
```
```swift
```swift
```swift
class AVMIDIChannelPressureEvent
```
```

An object that represents a MIDI channel pressure message.
```
```swift
```swift
```swift
class AVMIDIProgramChangeEvent
```
```

An object that represents a MIDI program or patch change message.
```
```swift
```swift
```swift
class AVMIDIPolyPressureEvent
```
```

An object that represents a MIDI poly or key pressure event.
```
```swift
```swift
```swift
class AVMIDIPitchBendEvent
```
```

An object that represents a MIDI pitch bend message.
```
```swift
```swift
```swift
class AVMIDIControlChangeEvent
```
```

An object that represents a MIDI control change message.
```
```

### [Managing Sequence Load Options](/documentation/AVFAudio/AVAudioSequencer#Managing-Sequence-Load-Options)

```swift
```swift
```swift
```swift
func load(from: Data, options: AVMusicSequenceLoadOptions) throws
```
```

Parses the data and adds its events to the sequence.
```
```swift
```swift
```swift
func load(from: URL, options: AVMusicSequenceLoadOptions) throws
```
```

Loads the file the URL references and adds the events to the sequence.
```
```swift
```swift
```swift
struct AVMusicSequenceLoadOptions
```
```

A structure that defines whether data on different MIDI channels map to multiple tracks, or whether the framework preserves the tracks as they are.
```
```

### [Operating an Audio Sequencer](/documentation/AVFAudio/AVAudioSequencer#Operating-an-Audio-Sequencer)

```swift
```swift
```swift
```swift
func prepareToPlay()
```
```

Gets ready to play the sequence by prerolling all events.
```
```swift
```swift
```swift
func start() throws
```
```

Starts the sequencer’s player.
```
```swift
```swift
```swift
func stop()
```
```

Stops the sequencer’s player.
```
```

### [Managing Time Stamps](/documentation/AVFAudio/AVAudioSequencer#Managing-Time-Stamps)

```swift
```swift
```swift
```swift
typealias AVMusicTimeStamp
```
```

A fractional number of beats.
```
```swift
```swift
```swift
func hostTime(forBeats: AVMusicTimeStamp, error: NSErrorPointer) -> UInt64
```
```

Gets the host time the sequence plays at the specified position.
```
```swift
```swift
```swift
func seconds(forBeats: AVMusicTimeStamp) -> TimeInterval
```
```

Gets the time for the specified beat position (timestamp) in the track, in seconds.
```
```

### [Handling Beat Range](/documentation/AVFAudio/AVAudioSequencer#Handling-Beat-Range)

```swift
```swift
```swift
```swift
func beats(forHostTime: UInt64, error: NSErrorPointer) -> AVMusicTimeStamp
```
```

Gets the beat the system plays at the specified host time.
```
```swift
```swift
```swift
func beats(forSeconds: TimeInterval) -> AVMusicTimeStamp
```
```

Gets the beat position (timestamp) for the specified time in the track.
```
```swift
```swift
```swift
var AVMusicTimeStampEndOfTrack: Double
```
```

A timestamp you use to access all events in a music track through a beat range.
```
```

### [Setting the User Callback](/documentation/AVFAudio/AVAudioSequencer#Setting-the-User-Callback)

```swift
```swift
```swift
```swift
func setUserCallback(AVAudioSequencerUserCallback?)
```
```

Adds a callback that the sequencer calls each time it encounters a user event during playback.
```
```swift
```swift
```swift
typealias AVAudioSequencerUserCallback
```
```

A callback the sequencer calls asynchronously during playback when it encounters a user event.
```
```

### [Getting Sequence Properties](/documentation/AVFAudio/AVAudioSequencer#Getting-Sequence-Properties)

```swift
```swift
```swift
```swift
var isPlaying: Bool
```
```

A Boolean value that indicates whether the sequencer’s player is in a playing state.
```
```swift
```swift
```swift
var rate: Float
```
```

The playback rate of the sequencer’s player.
```
```swift
```swift
```swift
var tracks: [AVMusicTrack]
```
```

An array that contains all the tracks in the sequence.
```
```swift
```swift
```swift
var currentPositionInBeats: TimeInterval
```
```

The current playback position, in beats.
```
```swift
```swift
```swift
var currentPositionInSeconds: TimeInterval
```
```

The current playback position, in seconds.
```
```swift
```swift
```swift
var tempoTrack: AVMusicTrack
```
```

The track that contains tempo information about the sequence.
```
```swift
```swift
```swift
var userInfo: [String : Any]
```
```

A dictionary that contains metadata from a sequence.
```
```swift
```swift
```swift
struct InfoDictionaryKey
```
```

Constants that defines metadata keys for a sequencer.
```
```swift
```swift
```swift
func data(withSMPTEResolution: Int, error: NSErrorPointer) -> Data
```
```

Gets a data object that contains the events from the sequence.
```
```swift
```swift
```swift
var AVMusicTimeStampEndOfTrack: Double
```
```

A timestamp you use to access all events in a music track through a beat range.
```
```

## [Relationships](/documentation/AVFAudio/AVAudioSequencer#relationships)

### [Inherits From](/documentation/AVFAudio/AVAudioSequencer#inherits-from)

*   [`NSObject`](/documentation/ObjectiveC/NSObject-swift.class)

### [Conforms To](/documentation/AVFAudio/AVAudioSequencer#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)

## [See Also](/documentation/AVFAudio/AVAudioSequencer#see-also)

### [MIDI](/documentation/AVFAudio/AVAudioSequencer#MIDI)

```swift
```swift
```swift
```swift
class AVAudioUnitSampler
```
```

An object that you configure with one or more instrument samples, based on Apple’s Sampler audio unit.
```
```