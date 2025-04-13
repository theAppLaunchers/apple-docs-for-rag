

- Foundation
- URLSessionTask
-  currentRequest 

Instance Property

# currentRequest

The URL request object currently being handled by the task.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var currentRequest: URLRequest? { get }
```

## Discussion

This value is typically the same as the initial request (originalRequest) except when the server has responded to the initial request with a redirect to a different URL.

## See Also

### Obtaining general task information

var originalRequest: URLRequest?

The original request object passed when the task was created.

var response: URLResponse?

The server’s response to the currently active request.

var taskDescription: String?

An app-provided string value for the current task.

var taskIdentifier: Int

An identifier uniquely identifying the task within a given session.

var error: (any Error)?

An error object that indicates why the task failed.

