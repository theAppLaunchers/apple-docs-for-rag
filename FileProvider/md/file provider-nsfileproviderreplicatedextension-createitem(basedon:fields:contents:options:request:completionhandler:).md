

- File Provider
- NSFileProviderReplicatedExtension
-  createItem(basedOn:fields:contents:options:request:completionHandler:) 

Instance Method

# createItem(basedOn:fields:contents:options:request:completionHandler:)

Tells the file provider to create or import an item based on a template.

iOS 16.0+iPadOS 16.0+macOS 11.0+visionOS 1.0+

``` source
func createItem(
    basedOn itemTemplate: NSFileProviderItem,
    fields: NSFileProviderItemFields,
    contents url: URL?,
    options: NSFileProviderCreateItemOptions = [],
    request: NSFileProviderRequest,
    completionHandler: @escaping (NSFileProviderItem?, NSFileProviderItemFields, Bool, (any Error)?) -> Void
) -> Progress
```

**Required**

## Parameters 

`itemTemplate`  

An object that defines the state of the new or imported item.

`fields`  

The fields that you should apply to the new or imported item.

`url`  

If the item is a file with the contents field set, this is the URL to the item’s content. Otherwise, it’s `nil`.

`options`  

The item creation options.

`request`  

An object that identifies the context of that request, such as the requesting app.

`completionHandler`  

A block that you call after uploading the item to your remote storage. You pass the following parameters:

`createdItem`  
The newly created item.

`stillPendingFields`  
Any fields that you haven’t yet applied. If you can apply all the fields at once, pass an empty `NSFileProviderItemField` instance.

`shouldFetchContent`  
A Boolean value that indicates whether the system should fetch the item’s content from your remote storage.

`error`  
If an error occurs, this object contains information about the error; otherwise, it’s `nil`.

## Return Value

A progress that tracks creating the item in your remote storage and uploading its content. The system automatically calls cancel() on the progress object when an error occurs.

## Discussion

The system calls this method when the user creates a new item or imports an item into the file provider. The system manages the local copy of the item. You’re responsible for syncing and saving the item to your remote storage.

Implement this method to create an item in your remote storage that matches the template, and then call the callback handler.

The `itemTemplate` parameter describes the item’s intended state, including:

filename  
The item’s name.

contentType  
The item’s type. The item can be a file, directory, symlink, or alias. UTTypeFolder, UTTypeSymbolicLink, and UTTypeAliasFile types typically need special handling.

parentItemIdentifier  
The item’s location.

The system sets the template’s itemIdentifier to a unique value and guarantees that it remains the same for the specified item. For example, the system can reuse the identifier to replay this method after a crash.

In general, set the properties in your `createdItem` to match the `itemTemplate`. One exception is the itemIdentifier property; always provide your own identifier for the item. If you reuse an existing identifier, the system replaces the local copy of the old item with the new one.

If the item is a document, fetch its contents from the `url` parameter. Otherwise, the `url` is `nil`. For symlinks, you can access the content using the template’s symlinkTargetPath parameter. For both symlinks and aliases, make sure to return the correct UTI for the item, because the UTI can’t be inferred from the item’s filename.

If you are reimporting an item and the system finds a local copy without any content, it sets the mayAlreadyExist option, and sets the `url` to nil. In this case, if you can’t match the item with an existing item from remote storage, pass `nil` as the completion handler’s `createdItem` parameter. The system then deletes the local copy of the item.

If the attempt to create an item fails because the parent directory doesn’t exist, pass NSFileProviderError.Code.noSuchItem to the handler. The system attempts to create the parent directory, and then tries to create the item again.

## See Also

### Managing Items

struct NSFileProviderCreateItemOptions

Options for creating items.

func modifyItem(NSFileProviderItem, baseVersion: NSFileProviderItemVersion, changedFields: NSFileProviderItemFields, contents: URL?, options: NSFileProviderModifyItemOptions, request: NSFileProviderRequest, completionHandler: (NSFileProviderItem?, NSFileProviderItemFields, Bool, (any Error)?) -> Void) -> Progress

Tells the file provider that an item’s content or metadata changed.

**Required**

struct NSFileProviderModifyItemOptions

Options for modifying items.

func deleteItem(identifier: NSFileProviderItemIdentifier, baseVersion: NSFileProviderItemVersion, options: NSFileProviderDeleteItemOptions, request: NSFileProviderRequest, completionHandler: ((any Error)?) -> Void) -> Progress

Tells the file provider to delete an item forever.

**Required**

struct NSFileProviderDeleteItemOptions

Options for deleting items.

