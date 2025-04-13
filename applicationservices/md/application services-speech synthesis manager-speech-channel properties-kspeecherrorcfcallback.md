

- Application Services
- Speech Synthesis Manager
- Speech-Channel Properties
-  kSpeechErrorCFCallBack 

Global Variable

# kSpeechErrorCFCallBack

Set the callback function to be called when an error is encountered during the processing of an embedded command.

macOS 10.5+

``` source
let kSpeechErrorCFCallBack: CFString
```

## Discussion

When a Speech Synthesis Manager function returns an error directly, the error callback function is not called. The callback function is passed information about the most recent error; it can determine information about the oldest pending error by using the speech information property `kSpeechErrorsProperty`. The value associated with this property is `CFNumber` object whose value is a pointer to an application-defined error callback function, whose syntax is described in SpeechErrorCFProcPtr. Passing a `CFNumber` object that contains the value `NULL` for the value of this property disables the error callback function.

This property works with the SetSpeechProperty(_:_:_:) function.

