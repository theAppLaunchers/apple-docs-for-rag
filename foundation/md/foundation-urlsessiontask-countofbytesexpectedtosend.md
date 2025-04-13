

- Foundation
- URLSessionTask
-  countOfBytesExpectedToSend 

Instance Property

# countOfBytesExpectedToSend

The number of bytes that the task expects to send in the request body.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var countOfBytesExpectedToSend: Int64 { get }
```

## Discussion

The URL loading system can determine the length of the upload data in three ways:

- From the length of the data object provided as the upload body.

- From the length of the file on disk provided as the upload body of an upload task (*not* a download task).

- From the `Content-Length` in the request object, if you explicitly set it.

Otherwise, the value is NSURLSessionTransferSizeUnknown (`-1`) if you provided a stream or body data object, or zero (`0`) if you did not.

## See Also

### Obtaining task progress

var progress: Progress

A representation of the overall task progress.

var countOfBytesExpectedToReceive: Int64

The number of bytes that the task expects to receive in the response body.

var countOfBytesReceived: Int64

The number of bytes that the task has received from the server in the response body.

var countOfBytesSent: Int64

The number of bytes that the task has sent to the server in the request body.

let NSURLSessionTransferSizeUnknown: Int64

The total size of the transfer cannot be determined.

