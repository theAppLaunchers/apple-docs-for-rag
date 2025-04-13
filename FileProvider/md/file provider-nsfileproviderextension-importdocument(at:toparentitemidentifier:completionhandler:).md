

- File Provider
- NSFileProviderExtension
-  importDocument(at:toParentItemIdentifier:completionHandler:) 

Instance Method

# importDocument(at:toParentItemIdentifier:completionHandler:)

Imports a file or package into the given parent directory.

iOS 11.0+iPadOS 11.0+visionOS 1.0+

``` source
func importDocument(
    at fileURL: URL,
    toParentItemIdentifier parentItemIdentifier: NSFileProviderItemIdentifier,
    completionHandler: @escaping (NSFileProviderItem?, (any Error)?) -> Void
)
```

``` source
func importDocument(
    at fileURL: URL,
    toParentItemIdentifier parentItemIdentifier: NSFileProviderItemIdentifier
) async throws -> NSFileProviderItem
```

## Parameters 

`fileURL`  

A security-scoped URL for the file to import. Call startAccessingSecurityScopedResource() on the URL before accessing it and stopAccessingSecurityScopedResource() when finished.

`parentItemIdentifier`  

The persistent identifier for the directory where the item will be imported.

`completionHandler`  

A block that takes the following parameters:

`importedDocumentItem`  
A provider item that describes the newly imported item, or `nil` if an error occurred.

`error`  
An error object. If an error occurs, pass in an object that describes the error; otherwise, set it to `nil`.

## Discussion

Important

You can call this method from synchronous code using a completion handler, as shown on this page, or you can call it as an asynchronous method that has the following declaration:

```
func importDocument(at fileURL: URL, toParentItemIdentifier parentItemIdentifier: NSFileProviderItemIdentifier) async throws -> NSFileProviderItem
```

For information about concurrency and asynchronous code in Swift, see Calling Objective-C APIs Asynchronously.

This method is called when the user imports a document or directory. Override this method to move the file at the provided security-scoped URL to the file provider’s storage. Your implementation should return immediately. Call the completion handler before performing any network activity or other long-running tasks. Defer these tasks to the background.

The `importedDocumentItem` instance that you pass to the completion handler must define the following properties:

itemIdentifier  
This identifier may be temporary. If you later receive a permanent identifier from your server, delete the temporary item and add the permanent one.

parentItemIdentifier  
Set to the value passed to the `parentItemIdentifier` parameter.

filename  
Set to the `fileURL` parameter’s nameKey resource value.

creationDate  
Set to the `fileURL` parameter’s creationDateKey resource value.

contentModificationDate  
Set to the `fileURL` parameter’s contentModificationDateKey resource value.

typeIdentifier  
Set to the `fileURL` parameter’s typeIdentifierKey resource value.

documentSize  
For a flat file, set to the `fileURL` parameter’s totalFileSizeKey resource value. For a package, set to the sum of the contents’ file sizes.

capabilities  
Set to define the actions that the user can perform on the directory (for example, allowsReading and allowsWriting).

The user’s ability to import an item into a directory is controlled by the parent directory’s allowsAddingSubItems capability.

## See Also

### Handling actions

Providing support for user-driven actions

Override methods to handle user-initiated actions.

func createDirectory(withName: String, inParentItemIdentifier: NSFileProviderItemIdentifier, completionHandler: (NSFileProviderItem?, (any Error)?) -> Void)

Creates a directory with the given name inside the given parent directory.

func deleteItem(withIdentifier: NSFileProviderItemIdentifier, completionHandler: ((any Error)?) -> Void)

Permanently deletes an item from the trash.

func renameItem(withIdentifier: NSFileProviderItemIdentifier, toName: String, completionHandler: (NSFileProviderItem?, (any Error)?) -> Void)

Renames a document or directory.

func reparentItem(withIdentifier: NSFileProviderItemIdentifier, toParentItemWithIdentifier: NSFileProviderItemIdentifier, newName: String?, completionHandler: (NSFileProviderItem?, (any Error)?) -> Void)

Moves the specified item into the given parent directory.

func setFavoriteRank(NSNumber?, forItemIdentifier: NSFileProviderItemIdentifier, completionHandler: (NSFileProviderItem?, (any Error)?) -> Void)

Marks a directory as a favorite and sets its relative order in the Favorites list.

func setLastUsedDate(Date?, forItemIdentifier: NSFileProviderItemIdentifier, completionHandler: (NSFileProviderItem?, (any Error)?) -> Void)

Marks an item as recently used and sets its relative order in the Recents list.

func setTagData(Data?, forItemIdentifier: NSFileProviderItemIdentifier, completionHandler: (NSFileProviderItem?, (any Error)?) -> Void)

Tags an item.

func trashItem(withIdentifier: NSFileProviderItemIdentifier, completionHandler: (NSFileProviderItem?, (any Error)?) -> Void)

Moves an item into the trash.

func untrashItem(withIdentifier: NSFileProviderItemIdentifier, toParentItemIdentifier: NSFileProviderItemIdentifier?, completionHandler: (NSFileProviderItem?, (any Error)?) -> Void)

Moves an item out of the trash.

