

- Application Services
- Speech Synthesis Manager
- Speech-Channel Properties
-  kSpeechNumberModeProperty 

Global Variable

# kSpeechNumberModeProperty

Get or set the speech channel’s current number-processing mode.

macOS 10.5+

``` source
let kSpeechNumberModeProperty: CFString
```

## Discussion

The value associated with this property is a `CFString` object that specifies whether the speech channel is currently in normal or literal number-processing mode. The constants `kSpeechModeNormal` and `kSpeechModeLiteral` (defined in Speech-Channel Modes for Core Foundation-based Functions) are the possible values of this string.

When the number-processing mode is `kSpeechModeNormal`, the synthesizer assembles digits into numbers (so that “12” is spoken as “twelve”). When the mode is `kSpeechModeLiteral`, each digit is spoken literally (so that “12” is spoken as “one, two”).

This property works with the CopySpeechProperty(_:_:_:) and SetSpeechProperty(_:_:_:) functions.

