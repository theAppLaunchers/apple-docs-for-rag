

- File Provider
- NSFileProviderIncrementalContentFetching
-  fetchContents(for:version:usingExistingContentsAt:existingVersion:request:completionHandler:) 

Instance Method

# fetchContents(for:version:usingExistingContentsAt:existingVersion:request:completionHandler:)

Asks the file provider for an update of the specified item.

iOS 16.0+iPadOS 16.0+macOS 11.0+visionOS 1.0+

``` source
func fetchContents(
    for itemIdentifier: NSFileProviderItemIdentifier,
    version requestedVersion: NSFileProviderItemVersion?,
    usingExistingContentsAt existingContents: URL,
    existingVersion: NSFileProviderItemVersion,
    request: NSFileProviderRequest,
    completionHandler: @escaping (URL?, NSFileProviderItem?, (any Error)?) -> Void
) -> Progress
```

**Required**

## Parameters 

`itemIdentifier`  

The identifier of the item this method should fetch from your remote server.

`requestedVersion`  

The new version. If this value is set, you must fetch the specified version, or fail with an error. If this value isn’t set, fetch the most recent version from your server.

`existingContents`  

A URL that points to the content of the currently cached item.

`existingVersion`  

The version of the currently cached item.

`request`  

An object that identifies the context of that request, such as the requesting app.

`completionHandler`  

A block that you call after downloading the update. Pass the following parameters:

`fileContents`  
A URL that points to the new contents, or `nil` if an error occurs.

`item`  
The item’s identifier, or `nil` if an error occurs. The item’s version must match the version of the content passed to the `fileContents` parameter.

`error`  
If an error occurs, this object contains information about the error; otherwise, it’s `nil`.

## Return Value

An item that tracks the extension’s progress.

## Discussion

Implement this method to optimize downloading changes. Rather than downloading an entire new copy of the item, you can download just the changes from your remote storage.

The system can call this method when it has already cached an item and learns that a new version is available. It passes a copy of the locally stored item to the method. In your implementation of the method, download any updates, apply them to the existing content, and then pass the updated version to the completion handler.

