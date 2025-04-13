

- AVFAudio
- AVSpeechSynthesisProviderRequest
-  init(ssmlRepresentation:voice:) 

Initializer

# init(ssmlRepresentation:voice:)

Creates a request with a voice and a description.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
init(
    ssmlRepresentation text: String,
    voice: AVSpeechSynthesisProviderVoice
)
```

## Parameters 

`text`  

The description of the text to synthesize.

`voice`  

The voice to use in the speech request.

