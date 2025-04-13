

- Foundation
- NSURLConnectionDownloadDelegate
-  connection(\_:didWriteData:totalBytesWritten:expectedTotalBytes:) 

Instance Method

# connection(\_:didWriteData:totalBytesWritten:expectedTotalBytes:)

Sent to the delegate to deliver progress information for a download of a URL asset to a destination file.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.2+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
optional func connection(
    _ connection: NSURLConnection,
    didWriteData bytesWritten: Int64,
    totalBytesWritten: Int64,
    expectedTotalBytes: Int64
)
```

## Parameters 

`connection`  

The URL connection object downloading the asset.

`bytesWritten`  

The number of bytes written since the last call of this method.

`totalBytesWritten`  

The total number of bytes of the downloading asset that have been written to the file.

`expectedTotalBytes`  

The total number of bytes of the URL asset once it is completely downloaded and written to a file. This parameter can be zero if the total number of bytes is not known.

## Discussion

This method is invoked repeatedly during the download of a URL asset to the destination file. The delegate typically uses the values of the three “bytes” parameters to update a progress indicator in the application’s user interface.

## See Also

### Managing Downloads of URL Assets

func connectionDidResumeDownloading(NSURLConnection, totalBytesWritten: Int64, expectedTotalBytes: Int64)

Sent to the delegate when an URL connection resumes downloading a URL asset that was earlier suspended.

func connectionDidFinishDownloading(NSURLConnection, destinationURL: URL)

Sent to the delegate when the URL connection has successfully downloaded the URL asset to a destination file.

**Required**

