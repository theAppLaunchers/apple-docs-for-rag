

- Foundation
- URLSessionDownloadDelegate
-  urlSession(\_:downloadTask:didWriteData:totalBytesWritten:totalBytesExpectedToWrite:) 

Instance Method

# urlSession(\_:downloadTask:didWriteData:totalBytesWritten:totalBytesExpectedToWrite:)

Periodically informs the delegate about the download’s progress.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
optional func urlSession(
    _ session: URLSession,
    downloadTask: URLSessionDownloadTask,
    didWriteData bytesWritten: Int64,
    totalBytesWritten: Int64,
    totalBytesExpectedToWrite: Int64
)
```

## Parameters 

`session`  

The session containing the download task.

`downloadTask`  

The download task.

`bytesWritten`  

The number of bytes transferred since the last time this delegate method was called.

`totalBytesWritten`  

The total number of bytes transferred so far.

`totalBytesExpectedToWrite`  

The expected length of the file, as provided by the `Content-Length` header. If this header was not provided, the value is NSURLSessionTransferSizeUnknown.

## Mentioned in 

Downloading files from websites

