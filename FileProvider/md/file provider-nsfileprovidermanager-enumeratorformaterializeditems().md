

- File Provider
- NSFileProviderManager
-  enumeratorForMaterializedItems() 

Instance Method

# enumeratorForMaterializedItems()

Returns an enumerator for all the items the system currently stores on disk.

iOS 16.0+iPadOS 16.0+macOS 11.0+visionOS 1.0+

``` source
func enumeratorForMaterializedItems() -> any NSFileProviderEnumerator
```

## Mentioned in 

Synchronizing the File Provider Extension

## Discussion

In most cases, the system requests an enumerator from the File Provider. The file provider creates the enumerator, and uses it to pass information back to the system. In this case, however, the roles are reversed. The File Provider extension calls this method to request an enumerator from the system. The system then creates the enumerator and uses it to pass the list of items currently stored on disk back to the File Provider extension.

## See Also

### Working with items

func reimportItems(below: NSFileProviderItemIdentifier, completionHandler: ((any Error)?) -> Void)

Tells the system to reimport the item and its content recursively.

func evictItem(identifier: NSFileProviderItemIdentifier, completionHandler: ((any Error)?) -> Void)

Asks the system to remove an item from its cache.

func requestDownloadForItem(withIdentifier: NSFileProviderItemIdentifier, requestedRange: NSRange?) async throws

func requestDownloadForItem(withIdentifier: NSFileProviderItemIdentifier, requestedRange: NSRange?, completionHandler: ((any Error)?) -> Void)

func requestModification(of: NSFileProviderItemFields, forItemWithIdentifier: NSFileProviderItemIdentifier, options: NSFileProviderModifyItemOptions, completionHandler: ((any Error)?) -> Void)

func enumeratorForPendingItems() -> any NSFileProviderPendingSetEnumerator

Returns an enumerator for the set of pending items.

