

- Application Services
- Speech Synthesis Manager
- Speech-Channel Information Constants
-  soInputMode 

Global Variable

# soInputMode

macOS 10.0+

``` source
var soInputMode: OSType { get }
```

## Discussion

Get or set the speech channel’s current text-processingmode. The returned value specifies whether the channel is currentlyin text input mode or phoneme input mode. The `speechInfo` parameteris a pointer to a variable of type `OSType`,which specifies a text-processing mode. The constants modeText and modePhonemes specifythe available text-processing modes.

The `modeText` constantindicates that the speech channel is in text-processing mode. The `modePhonemes` constantindicates that the speech channel is in phoneme-processing mode.When in phoneme-processing mode, a text buffer is interpreted tobe a series of characters representing various phonemes and prosodiccontrols. Some synthesizers might support additional input-processingmodes and define constants for these modes.

When in text-processing mode, you can also specify how characters and numbers should be processed, using soCharacterMode and soNumberMode.

This selector works with both the `GetSpeechInfo` and `SetSpeechInfo` functions.

