

- Speech
- SFSpeechRecognitionTask
-  error 

Instance Property

# error

An error object that specifies the error that occurred during a speech recognition task.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.15+visionOS 1.0+

``` source
var error: (any Error)? { get }
```

## Discussion

The system may return one of the errors listed in the table below.

| Error Code | Error Domain | Description |
|----|----|----|
| `102` | `kLSRErrorDomain` | Assets are not installed. |
| `201` | `kLSRErrorDomain` | Siri or Dictation is disabled. |
| `300` | `kLSRErrorDomain` | Failed to initialize recognizer. |
| `301` | `kLSRErrorDomain` | Request was canceled. |
| `203` | `kAFAssistantErrorDomain` | Failure occurred during speech recognition. |
| `1100` | `kAFAssistantErrorDomain` | Trying to start recognition while an earlier instance is still active. |
| `1101` | `kAFAssistantErrorDomain` | Connection to speech process was invalidated. |
| `1107` | `kAFAssistantErrorDomain` | Connection to speech process was interrupted. |
| `1110` | `kAFAssistantErrorDomain` | Failed to recognize any speech. |
| `1700` | `kAFAssistantErrorDomain` | Request is not authorized. |

## See Also

### Monitoring Recognition Progress

var state: SFSpeechRecognitionTaskState

The current state of the speech recognition task.

enum SFSpeechRecognitionTaskState

The state of the task associated with the recognition request.

