

- Foundation
- NSNotification
- NSNotification.Name
-  NSPersistentStoreCoordinatorWillRemoveStore 

Type Property

# NSPersistentStoreCoordinatorWillRemoveStore

A notification that posts before a coordinator removes a store.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
static let NSPersistentStoreCoordinatorWillRemoveStore: NSNotification.Name
```

## Discussion

This notification’s `object` is the changed store coordinator. The framework posts the notification to an internal thread. Don’t peform any asynchronous work or block the calling thread.

There is no `userInfo` dictionary.

## See Also

### Core Data

static let NSManagedObjectContextDidSave: NSNotification.Name

A notification that posts after a context finishes writing unsaved changes.

static let NSManagedObjectContextObjectsDidChange: NSNotification.Name

A notification that posts when there are changes to context’s registered managed objects.

static let NSManagedObjectContextWillSave: NSNotification.Name

A notification that posts before a context writes unsaved changes.

static let NSPersistentStoreCoordinatorStoresDidChange: NSNotification.Name

A notification that the coordinator posts after its registered stores change.

static let NSPersistentStoreCoordinatorStoresWillChange: NSNotification.Name

A notification that posts before a coordinator changes its registered stores.

static let NSCoreDataCoreSpotlightDelegateIndexDidUpdate: NSNotification.Name

A notification that posts after Spotlight completes an index update.

static let NSManagedObjectContextDidMergeChangesObjectIDs: NSNotification.Name

A notification that posts after a context merges changes from a different notification.

static let NSManagedObjectContextDidSaveObjectIDs: NSNotification.Name

A notification that posts after a context finishes writing changes.

static let NSPersistentStoreRemoteChange: NSNotification.Name

A notification that posts after another process writes to a persistent store.

static let NSPersistentStoreDidImportUbiquitousContentChanges: NSNotification.Name

Posted after records are imported from the ubiquitous content store.

Deprecated

