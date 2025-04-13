

- Speech
- SFSpeechRecognizer
-  recognitionTask(with:delegate:) 

Instance Method

# recognitionTask(with:delegate:)

Recognizes speech from the audio source associated with the specified request, using the specified delegate to manage the results.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.15+visionOS 1.0+

``` source
func recognitionTask(
    with request: SFSpeechRecognitionRequest,
    delegate: any SFSpeechRecognitionTaskDelegate
) -> SFSpeechRecognitionTask
```

## Parameters 

`request`  

A request (encapsulated in an SFSpeechRecognitionRequest object) to recognize speech from an audio source.

`delegate`  

An object that can handle results from the speech recognition task. This object must conform to the SFSpeechRecognitionTaskDelegate protocol.

## Return Value

The task object you can use to manage an in-progress recognition request.

## Discussion

Use this method to initiate the speech recognition process on the audio contained in the request object. This method executes asynchronously and returns a SFSpeechRecognitionTask object that you can use to cancel or finalize the recognition process later. As results become available, the method calls the methods of the provided `delegate` object.

Note that the SFSpeechRecognitionTask object returned by this method does not retain your delegate object. You must maintain a strong reference to your delegate while speech recognition is in progress.

## See Also

### Performing Speech Recognition on Audio

func recognitionTask(with: SFSpeechRecognitionRequest, resultHandler: (SFSpeechRecognitionResult?, (any Error)?) -> Void) -> SFSpeechRecognitionTask

Executes the speech recognition request and delivers the results to the specified handler block.

protocol SFSpeechRecognitionTaskDelegate

A protocol with methods for managing multi-utterance speech recognition requests.

