

- Foundation
- URLCache
-  getCachedResponse(for:completionHandler:) 

Instance Method

# getCachedResponse(for:completionHandler:)

Gets the cached URL response for a data task, passing it to the provided completion handler.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func getCachedResponse(
    for dataTask: URLSessionDataTask,
    completionHandler: @escaping (CachedURLResponse?) -> Void
)
```

``` source
func cachedResponse(for dataTask: URLSessionDataTask) async -> CachedURLResponse?
```

## Parameters 

`dataTask`  

The data task whose cached URL response is desired.

`completionHandler`  

A completion handler that receives the cached URL response for the data task’s request, or `nil` if no response is found in the cache.

## See Also

### Getting and storing cached objects

func cachedResponse(for: URLRequest) -> CachedURLResponse?

Returns the cached URL response in the cache for the specified URL request.

func storeCachedResponse(CachedURLResponse, for: URLRequest)

Stores a cached URL response for a specified request.

func storeCachedResponse(CachedURLResponse, for: URLSessionDataTask)

Stores a cached URL response for a specified data task.

