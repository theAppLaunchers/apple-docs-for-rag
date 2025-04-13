

- Core Data
- NSManagedObjectContext
-  didMergeChangesObjectIDsNotification 

Type Property

# didMergeChangesObjectIDsNotification

A notification that posts after a context finishes merging changes from another notification.

iOS 10.3+iPadOS 10.3+Mac CatalystmacOS 10.12+tvOS 10.2+visionOSwatchOS 3.2+

``` source
static let didMergeChangesObjectIDsNotification: Notification.Name
```

## Discussion

This notification’s `object` is the merged context. Don’t peform any asynchronous work or block the calling thread. NSManagedObjectContext posts notifications to the same thread that creates it.

The `userInfo` dictionary contains the identifiers of the inserted, updated, deleted, refreshed, and invalidated managed objects. For the keys to access those objects, see NSManagedObjectContext.NotificationKey. It’s safe to capture the dictionary’s contents.

## See Also

### Managing notifications

static let didChangeObjectsNotification: Notification.Name

A notification that posts when a context makes changes to its registered objects.

static let NSManagedObjectContextObjectsDidChange: NSNotification.Name

A notification that posts when there are changes to context’s registered managed objects.

static let didSaveObjectsNotification: Notification.Name

A notification that posts after a context completes a save.

static let NSManagedObjectContextDidSave: NSNotification.Name

A notification that posts after a context finishes writing unsaved changes.

static let willSaveObjectsNotification: Notification.Name

A notification that posts before a context writes pending changes to disk.

static let NSManagedObjectContextWillSave: NSNotification.Name

A notification that posts before a context writes unsaved changes.

let NSInsertedObjectsKey: String

A key for the set of objects that were inserted into the context.

let NSUpdatedObjectsKey: String

A key for the set of objects that were updated.

let NSDeletedObjectsKey: String

A key for the set of objects that were marked for deletion during the previous event.

let NSRefreshedObjectsKey: String

A key for the set of objects that were refreshed but were not dirtied in the scope of this context.

let NSInvalidatedObjectsKey: String

A key for the set of objects that were invalidated.

let NSInvalidatedAllObjectsKey: String

A key that specifies that all objects in the context have been invalidated.

static let didSaveObjectIDsNotification: Notification.Name

A notification that posts after a context finishes saving changes to its managed objects.

enum NotificationKey

Keys to access details in user info dictionaries of managed object context notifications.

