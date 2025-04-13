

- Application Services
- Speech Synthesis Manager
-  SpeechTextDoneProcPtr 

Type Alias

# SpeechTextDoneProcPtr

Defines a pointer to a text-done callback functionthat is called when the Speech Synthesis Manager has finished processinga buffer of text.

macOS 10.0+

``` source
typealias SpeechTextDoneProcPtr = (SpeechChannel, SRefCon, UnsafeMutablePointer?, UnsafeMutablePointer, UnsafeMutablePointer) -> Void
```

## Parameters 

`chan`  

The speech channel that has finished processing input text.

`refCon`  

The reference constant associated with the speech channel.

`nextBuf`  

On return, a pointer to the next buffer of text to process or `NULL` if your application has no additional text to be spoken. This parameter is mostly for internal use by the Speech Synthesis Manager.

`byteLen`  

On return, a pointer to the number of bytes of the text buffer pointed to by the `nextBuf` parameter.

`controlFlags`  

On return, a pointer to the control flags to be used in generating the next buffer of text.

## Discussion

If a text-done callback function is installed in a speechchannel, then the Speech Synthesis Manager calls this function whenit finishes processing a buffer of text. The Speech Synthesis Managermight not yet have completed finishing speaking the text and indeed mightnot have started speaking it.

You can specify a text-done callback function by passing the `soTextDoneCallBack` selector tothe `SetSpeechInfo` function.

A common use of a text-done callback function is to alertyour application once the text passed to the `SpeakText` or `SpeakBuffer` functioncan be disposed of (or, when the text is contained within a lockedrelocatable block, when the relocatable block can be unlocked). TheSpeech Synthesis Manager copies the text you pass to the `SpeakText` or `SpeakBuffer` functioninto an internal buffer. Once it has finished processing the text,you may dispose of the original text buffer, even if speech is notyet complete. However, if you wish to write a callback functionthat executes when speech is completed, see the definition of a speech-donecallback function below.

Although most applications will not need to, your callbackfunction can indicate to the Speech Synthesis Manager whether thereis another buffer of text to speak. If there is another buffer,your callback function should reference it by setting the `nextBuf` and `byteLen` parametersto appropriate values. (Your callback function might also changethe control flags to be used to process the speech by altering thevalue in the `controlFlags` parameter.)Setting these parameters allows the Speech Synthesis Manager togenerate uninterrupted speech. If there is no more text to speak,your callback function should set `nextBuf` to `NULL`.In this case, the Speech Synthesis Manager ignores the `byteLen` and `controlFlags` parameters.

If your text-done callback function does not change the valuesof the `nextBuf` and `byteLen` parameters,the text buffer just spoken will be spoken again.

## See Also

### Callbacks

typealias SpeechDoneProcPtr

Defines a pointer to a speech-done callback functionwhich is called when the Speech Synthesis Manager finishes speakinga buffer of text.

typealias SpeechErrorProcPtr

Defines a pointer to an error callback functionthat handles syntax errors within commands embedded in a text bufferbeing processed by the Speech Synthesis Manager.

typealias SpeechErrorCFProcPtr

Defines a pointer to an error callback function that handles syntax errors within commands embedded in a `CFString` object being processed by the Speech Synthesis Manager.

typealias SpeechPhonemeProcPtr

Defines a pointer to a phoneme callback functionthat is called by the Speech Synthesis Manager before it pronouncesa phoneme.

typealias SpeechSyncProcPtr

Defines a pointer to a synchronization callbackfunction that is called when the Speech Synthesis Manager encountersa synchronization command embedded in a text buffer.

typealias SpeechWordProcPtr

Defines a pointer to a word callback functionthat is called by the Speech Synthesis Manager before it pronouncesa word.

typealias SpeechWordCFProcPtr

Defines a pointer to a Core Foundation-based word callback function that is called by the Speech Synthesis Manager before it pronounces a word.

