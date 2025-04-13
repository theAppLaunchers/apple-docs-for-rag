

- AVFAudio
- AVSpeechSynthesisVoice
-  currentLanguageCode() 

Type Method

# currentLanguageCode()

Returns the language and locale code for the user’s current locale.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.14+tvOSvisionOS 1.0+watchOS 2.0+

``` source
class func currentLanguageCode() -> String
```

## Return Value

A string that contains the BCP 47 language and locale code for the user’s current locale.

## Discussion

This code reflects the user’s language and region preferences in the Settings app.

## See Also

### Working with language codes

var language: String

A BCP 47 code that contains the voice’s language and locale.

