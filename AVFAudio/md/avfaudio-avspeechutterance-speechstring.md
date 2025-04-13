

- AVFAudio
- AVSpeechUtterance
-  speechString 

Instance Property

# speechString

A string that contains the text for speech synthesis.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.14+tvOSvisionOS 1.0+watchOS 2.0+

``` source
var speechString: String { get }
```

## Discussion

You can’t change an utterance’s text after initializaiton. If you want the speech synthesizer to speak different text, create a new utterance.

## See Also

### Inspecting utterance text

var attributedSpeechString: NSAttributedString

An attributed string that contains the text for speech synthesis.

