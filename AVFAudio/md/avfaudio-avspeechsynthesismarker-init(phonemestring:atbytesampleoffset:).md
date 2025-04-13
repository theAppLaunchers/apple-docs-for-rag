

- AVFAudio
- AVSpeechSynthesisMarker
-  init(phonemeString:atByteSampleOffset:) 

Initializer

# init(phonemeString:atByteSampleOffset:)

Creates a phoneme marker with a range of the phoneme and offset into the audio buffer.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
init(
    phonemeString phoneme: String,
    atByteSampleOffset byteSampleOffset: Int
)
```

## Parameters 

`phoneme`  

A string that represents a distinct sound.

`byteSampleOffset`  

The byte offset into the audio buffer.

## See Also

### Creating a marker

init(markerType: AVSpeechSynthesisMarker.Mark, forTextRange: NSRange, atByteSampleOffset: Int)

Creates a marker with a type and location of the request’s text.

init(wordRange: NSRange, atByteSampleOffset: Int)

Creates a word marker with a range of the word and offset into the audio buffer.

init(sentenceRange: NSRange, atByteSampleOffset: Int)

Creates a sentence marker with a range of the sentence and offset into the audio buffer.

init(paragraphRange: NSRange, atByteSampleOffset: Int)

Creates a paragraph marker with a range of the paragraph and offset into the audio buffer.

init(bookmarkName: String, atByteSampleOffset: Int)

Creates a bookmark marker with a name and offset into the audio buffer.

