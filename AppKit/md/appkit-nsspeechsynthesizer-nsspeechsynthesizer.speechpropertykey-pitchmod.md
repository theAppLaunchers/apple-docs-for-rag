

- AppKit
- NSSpeechSynthesizer
- NSSpeechSynthesizer.SpeechPropertyKey
-  pitchMod 

Type Property

# pitchMod

Get or set a synthesizer’s pitch modulation.

macOS 10.5+

``` source
static let pitchMod: NSSpeechSynthesizer.SpeechPropertyKey
```

## Discussion

An NSNumber object that specifies the synthesizer’s pitch modulation.

Pitch modulation is also expressed as a floating-point value in the range of 0.000 to 127.000. These values correspond to MIDI note values, where 60.000 is equal to middle C on a piano scale. The most useful speech pitches fall in the range of 40.000 to 55.000. A pitch modulation value of 0.000 corresponds to a monotone in which all speech is generated at the frequency corresponding to the speech pitch. Given a speech pitch value of 46.000, a pitch modulation of 2.000 would mean that the widest possible range of pitches corresponding to the actual frequency of generated text would be 44.000 to 48.000.

This property is used with setObject(_:forProperty:) and object(forProperty:).

Note

The change in pitch modulation may not be noticeable until the next sentence or paragraph is spoken.

## See Also

### Speech Property Keys

static let status: NSSpeechSynthesizer.SpeechPropertyKey

Get speech-status information for the synthesizer.

static let errors: NSSpeechSynthesizer.SpeechPropertyKey

Get speech-error information for the synthesizer.

static let inputMode: NSSpeechSynthesizer.SpeechPropertyKey

Get or set the synthesizer’s current text-processing mode.

static let characterMode: NSSpeechSynthesizer.SpeechPropertyKey

Get or set the synthesizer’s current text-processing mode.

static let numberMode: NSSpeechSynthesizer.SpeechPropertyKey

Get or set the synthesizer’s current number-processing mode.

static let rate: NSSpeechSynthesizer.SpeechPropertyKey

Get or set a synthesizer’s speech rate.

static let pitchBase: NSSpeechSynthesizer.SpeechPropertyKey

Get or set a synthesizer’s baseline speech pitch.

static let volume: NSSpeechSynthesizer.SpeechPropertyKey

Get or set the speech volume for a synthesizer.

static let synthesizerInfo: NSSpeechSynthesizer.SpeechPropertyKey

Get information about the speech synthesizer being used on the specified synthesizer.

static let recentSync: NSSpeechSynthesizer.SpeechPropertyKey

Get the message code for the most recently encountered synchronization command.

static let phonemeSymbols: NSSpeechSynthesizer.SpeechPropertyKey

Get a list of phoneme symbols and example words defined for the synthesizer.

static let currentVoice: NSSpeechSynthesizer.SpeechPropertyKey

Set the current voice on the synthesizer to the specified voice.

static let commandDelimiter: NSSpeechSynthesizer.SpeechPropertyKey

Set the embedded speech command delimiter characters to be used for the synthesizer.

static let reset: NSSpeechSynthesizer.SpeechPropertyKey

Set a synthesizer back to its default state.

static let outputToFileURL: NSSpeechSynthesizer.SpeechPropertyKey

Set the speech output destination to a file or to the computer’s speakers.

