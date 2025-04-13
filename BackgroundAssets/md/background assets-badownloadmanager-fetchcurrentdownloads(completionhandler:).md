

- Background Assets
- BADownloadManager
-  fetchCurrentDownloads(completionHandler:) 

Instance Method

# fetchCurrentDownloads(completionHandler:)

Fetches the contents of the manager’s download queue.

iOS 16.1+iPadOS 16.1+Mac Catalyst 16.1+macOS 13.0+tvOS 18.4+visionOS 2.4+

``` source
func fetchCurrentDownloads(completionHandler: @escaping ([BADownload], (any Error)?) -> Void)
```

``` source
var currentDownloads: [BADownload] { get async throws }
```

## Parameters 

`completionHandler`  

The handler that processes the fetch results, which the system executes on an arbitrary queue.

## Discussion

Concurrency Note

You can call this method from synchronous code using a completion handler, as this page explains, or you can call it as an asynchronous method that has the following declaration:

```
var currentDownloads: [BADownload] { get async throws }
```

For information about concurrency and asynchronous code in Swift, see Calling Objective-C APIs Asynchronously.

The completion handler takes the following parameters:

- An array of scheduled and in-progress downloads.

- An error if a problems occurs, or `nil` if the method successfully fetches the current downloads.

## See Also

### Fetching in-progress downloads

func fetchCurrentDownloads() throws -> [BADownload]

