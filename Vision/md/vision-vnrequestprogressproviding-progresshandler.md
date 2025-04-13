

- Vision
- VNRequestProgressProviding
-  progressHandler 

Instance Property

# progressHandler

A block of code executed periodically during a Vision request to report progress on long-running tasks.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+macOS 10.15+tvOS 13.0+visionOS 1.0+

``` source
var progressHandler: VNRequestProgressHandler { get set }
```

**Required**

## Discussion

The progress handler is an optional method that allows clients of the request to report progress to the user or to display partial results as they become available. The Vision framework may call this handler on a different dispatch queue from the thread on which you initiated the original request, so ensure that your handler can execute asynchronously, in a thread-safe manner.

## See Also

### Tracking Progress

var indeterminate: Bool

A Boolean set to true when a request can’t determine its progress in fractions completed.

**Required**

