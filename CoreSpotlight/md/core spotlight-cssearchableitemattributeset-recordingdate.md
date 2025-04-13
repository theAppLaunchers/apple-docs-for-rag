

- Core Spotlight
- CSSearchableItemAttributeSet
-  recordingDate 

Instance Property

# recordingDate

The recording date of the song or composition.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+visionOS 1.0+

``` source
var recordingDate: Date? { get set }
```

## Discussion

This property contains the original recording date of the song or composition and is supplementary to contentCreationDate, which indicates the date of an edited or optimized version.

## See Also

### Describing music

var album: String?

The title for a collection of audio media.

var artist: String?

The artist associated with the media.

var audioChannelCount: NSNumber?

The number of channels in the audio data that the file contains.

var audioEncodingApplication: String?

The name of the application that encoded the data the audio file contains.

var audioSampleRate: NSNumber?

The sample rate of the audio data the file contains, as a float value representing Hz (audio frames per second), such as 44100.0 or 22254.54.

var audioTrackNumber: NSNumber?

The track number of a song or audio composition when part of an album.

var composer: String?

The composer of the song or audio composition that the audio file contains.

var keySignature: String?

The musical key of the song or audio composition that the file contains, such as C, Dm, or F#m.

var lyricist: String?

The lyricist or text writer for the song or audio composition that the file contains.

var musicalGenre: String?

The musical genre of the song or audio composition that the file contains, such as jazz, pop, rock, or classical.

var tempo: NSNumber?

The tempo of the music that the audio file contains, in beats per minute.

var timeSignature: String?

The time signature of the musical composition that the audio or MIDI file contains, in a string, such as “4/4” or “7/8”.

var generalMIDISequence: NSNumber?

A value that indicates whether the MIDI sequence the file contains is set up for use with a general MIDI device.

var musicalInstrumentCategory: String?

The category of the instrument associated with the audio file.

var musicalInstrumentName: String?

The name of an instrument within the context of an instrument category.

