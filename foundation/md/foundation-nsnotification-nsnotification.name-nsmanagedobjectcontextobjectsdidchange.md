

- Foundation
- NSNotification
- NSNotification.Name
-  NSManagedObjectContextObjectsDidChange 

Type Property

# NSManagedObjectContextObjectsDidChange

A notification that posts when there are changes to context’s registered managed objects.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.1+macOS 10.4+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
static let NSManagedObjectContextObjectsDidChange: NSNotification.Name
```

## Discussion

Note

This notification posts only when there are changes to the context’s registered managed objects. It doesn’t post when a fetch adds managed objects to the context.

This notification’s `object` property is the changed managed object context. Don’t peform any asynchronous work or block the calling thread. NSManagedObjectContext posts notifications to the same thread that creates it.

The `userInfo` dictionary contains the inserted, updated, deleted, and invalidated managed objects. For the keys to access those objects, see NSManagedObjectContext.NotificationKey. Don’t capture the dictionary’s contents.

## See Also

### Core Data

static let NSManagedObjectContextDidSave: NSNotification.Name

A notification that posts after a context finishes writing unsaved changes.

static let NSManagedObjectContextWillSave: NSNotification.Name

A notification that posts before a context writes unsaved changes.

static let NSPersistentStoreCoordinatorStoresDidChange: NSNotification.Name

A notification that the coordinator posts after its registered stores change.

static let NSPersistentStoreCoordinatorStoresWillChange: NSNotification.Name

A notification that posts before a coordinator changes its registered stores.

static let NSPersistentStoreCoordinatorWillRemoveStore: NSNotification.Name

A notification that posts before a coordinator removes a store.

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

