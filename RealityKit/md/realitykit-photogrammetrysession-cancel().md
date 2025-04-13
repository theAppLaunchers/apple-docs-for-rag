

- RealityKit
- PhotogrammetrySession
-  cancel() 

Instance Method

# cancel()

Requests cancellation of any running requests.

iOS 17.0+iPadOS 17.0+Mac Catalyst 15.0+macOS 12.0+

``` source
func cancel()
```

## Discussion

When cancellation has completed, a `.processingCancelled` message will be output and `isProcessing` will be `false`. Calling this method has no effect if `!isProcessing`.

Note

This call is asynchronous and it may take some time before the pipeline fully stops, resources are reclaimed, and the error is actually produced, so callers should monitor `output` for the message before making a new session.

## See Also

### Controlling object creation

func process(requests: [PhotogrammetrySession.Request]) throws

Starts processing of the provided processing `requests`. Messages begin to be produced to the `output` publisher.

