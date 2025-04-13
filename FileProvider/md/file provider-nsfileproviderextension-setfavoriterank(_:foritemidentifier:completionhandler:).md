

- File Provider
- NSFileProviderExtension
-  setFavoriteRank(\_:forItemIdentifier:completionHandler:) 

Instance Method

# setFavoriteRank(\_:forItemIdentifier:completionHandler:)

Marks a directory as a favorite and sets its relative order in the Favorites list.

iOS 11.0+iPadOS 11.0+visionOS 1.0+

``` source
func setFavoriteRank(
    _ favoriteRank: NSNumber?,
    forItemIdentifier itemIdentifier: NSFileProviderItemIdentifier,
    completionHandler: @escaping (NSFileProviderItem?, (any Error)?) -> Void
)
```

``` source
func setFavoriteRank(
    _ favoriteRank: NSNumber?,
    forItemIdentifier itemIdentifier: NSFileProviderItemIdentifier
) async throws -> NSFileProviderItem
```

## Parameters 

`favoriteRank`  

A value used to determine the relative order of directories in the Favorites list.

`itemIdentifier`  

The item’s persistent identifier.

`completionHandler`  

A block that takes the following parameters:

`favoriteItem`  
A file provider item that represents the changed item, or `nil` if an error occurred.

`error`  
An error object. If an error occurs, pass in an object that describes the error; otherwise, set it to `nil`.

## Discussion

Important

You can call this method from synchronous code using a completion handler, as shown on this page, or you can call it as an asynchronous method that has the following declaration:

```
func setFavoriteRank(_ favoriteRank: NSNumber?, forItemIdentifier itemIdentifier: NSFileProviderItemIdentifier) async throws -> NSFileProviderItem
```

For information about concurrency and asynchronous code in Swift, see Calling Objective-C APIs Asynchronously.

This method is called when the user marks a directory as a favorite. Override this method to make any necessary local changes. Your implementation should return immediately. Call the completion handler before performing any network activity or other long-running tasks. Defer these tasks to the background.

The `favoriteItem` instance that you pass to the completion handler should match the item’s old file provider item, with only one change: set the favoriteRank property with the value of the `favoriteRank` parameter.

Always include items with a non-`nil` favoriteRank property in your File Provider extension’s working set; however, you don’t need to include the directory’s content. You also don’t need to make the directory’s content available offline.

## See Also

### Handling actions

Providing support for user-driven actions

Override methods to handle user-initiated actions.

func createDirectory(withName: String, inParentItemIdentifier: NSFileProviderItemIdentifier, completionHandler: (NSFileProviderItem?, (any Error)?) -> Void)

Creates a directory with the given name inside the given parent directory.

func deleteItem(withIdentifier: NSFileProviderItemIdentifier, completionHandler: ((any Error)?) -> Void)

Permanently deletes an item from the trash.

func importDocument(at: URL, toParentItemIdentifier: NSFileProviderItemIdentifier, completionHandler: (NSFileProviderItem?, (any Error)?) -> Void)

Imports a file or package into the given parent directory.

func renameItem(withIdentifier: NSFileProviderItemIdentifier, toName: String, completionHandler: (NSFileProviderItem?, (any Error)?) -> Void)

Renames a document or directory.

func reparentItem(withIdentifier: NSFileProviderItemIdentifier, toParentItemWithIdentifier: NSFileProviderItemIdentifier, newName: String?, completionHandler: (NSFileProviderItem?, (any Error)?) -> Void)

Moves the specified item into the given parent directory.

func setLastUsedDate(Date?, forItemIdentifier: NSFileProviderItemIdentifier, completionHandler: (NSFileProviderItem?, (any Error)?) -> Void)

Marks an item as recently used and sets its relative order in the Recents list.

func setTagData(Data?, forItemIdentifier: NSFileProviderItemIdentifier, completionHandler: (NSFileProviderItem?, (any Error)?) -> Void)

Tags an item.

func trashItem(withIdentifier: NSFileProviderItemIdentifier, completionHandler: (NSFileProviderItem?, (any Error)?) -> Void)

Moves an item into the trash.

func untrashItem(withIdentifier: NSFileProviderItemIdentifier, toParentItemIdentifier: NSFileProviderItemIdentifier?, completionHandler: (NSFileProviderItem?, (any Error)?) -> Void)

Moves an item out of the trash.

