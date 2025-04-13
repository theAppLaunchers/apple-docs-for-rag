

- Speech
-  SFSpeechURLRecognitionRequest 

Class

# SFSpeechURLRecognitionRequest

A request to recognize speech in a recorded audio file.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.15+visionOS 1.0+

``` source
class SFSpeechURLRecognitionRequest
```

## Overview

Use this object to perform speech recognition on the contents of an audio file.

The following example shows a method that performs recognition on an audio file based on the user’s default language and prints out the transcription.

Listing 1. Getting a speech recognizer and making a recognition request

```
func recognizeFile(url: URL) {
    // Create a speech recognizer associated with the user's default language.
    guard let myRecognizer = SFSpeechRecognizer() else {
        // The system doesn't support the user's default language.
        return
    }

    guard myRecognizer.isAvailable else {
        // The recognizer isn't available.
        return
    }

    // Create and execute a speech recognition request for the audio file at the URL.
    let request = SFSpeechURLRecognitionRequest(url: url)
    myRecognizer.recognitionTask(with: request) { (result, error) in
        guard let result else {
            // Recognition failed, so check the error for details and handle it.
            return
        }

        // Print the speech transcription with the highest confidence that the
        // system recognized.
        if result.isFinal {
            print(result.bestTranscription.formattedString)
        }
    }
}
```

## Topics

### Creating a Speech Recognition Request

init(url: URL)

Creates a speech recognition request, initialized with the specified URL.

### Accessing the URL of the Audio File

var url: URL

The URL of the audio file.

## Relationships

### Inherits From

- SFSpeechRecognitionRequest

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol

## See Also

### Audio sources

Recognizing speech in live audio

Perform speech recognition on audio coming from the microphone of an iOS device.

class SFSpeechAudioBufferRecognitionRequest

A request to recognize speech from captured audio content, such as audio from the device’s microphone.

class SFSpeechRecognitionRequest

An abstract class that represents a request to recognize speech from an audio source.

