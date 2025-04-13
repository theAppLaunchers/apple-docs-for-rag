

- Core Data
-  NSBatchDeleteRequest 

Class

# NSBatchDeleteRequest

A request that deletes objects in the SQLite persistent store without loading them into memory.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
class NSBatchDeleteRequest
```

## Overview

`NSBatchDeleteRequest` — available only when using a SQLite persistent store — deletes managed objects at the SQL level of the persistent store. This request is quicker and more efficient than using a context to fetch a large number of objects into memory, delete them, and then save those deletions back to the store. You create a request using an instance of NSFetchRequest that identifies the objects to delete. Alternatively, you can provide an array of identifiers from specific objects of the same entity type; mixing entity types results in an error when you execute the request.

NSManagedObjectContext doesn’t automatically merge a request’s deletions because they happen at the SQL level. Subsequently, you must remove any deleted objects from memory after the request finishes. To determine the objects a request deletes, configure it to return the NSManagedObjectID of each deleted object and use those identifiers to update your contexts, as the following example shows:

```
// Configure the request to return the IDs of the objects it deletes.
request.resultType = .resultTypeObjectIDs

do {
    // Execute the request.
    let deleteResult = try context.execute(request) as? NSBatchDeleteResult

    // Extract the IDs of the deleted managed objectss from the request's result.
    if let objectIDs = deleteResult?.result as? [NSManagedObjectID] {

        // Merge the deletions into the app's managed object context.
        NSManagedObjectContext.mergeChanges(
            fromRemoteContextSave: [NSDeletedObjectsKey: objectIDs],
            into: [context]
        )
    }
} catch {
    // Handle any thrown errors.
}
```

Alternatively, you can use persistent history tracking to make your contexts aware of changes that happen at the persistent store level. For more information, see Consuming relevant store changes.

Important

Ensure that a request’s changes don’t violate the validation rules in your data model beyond basic delete rules, such as reducing a relationship count below the specified minimum. The Deny delete rule isn’t compatible with `NSBatchDeleteRequest`.

## Topics

### Creating a Request

init(fetchRequest: NSFetchRequest&lt;any NSFetchRequestResult>)

Creates a request that deletes the results of the specified fetch request.

convenience init(objectIDs: [NSManagedObjectID])

Creates a request that deletes the managed objects with the specified identifiers.

### Accessing the Fetch Request

var fetchRequest: NSFetchRequest&lt;any NSFetchRequestResult>

The fetch request that identifies the managed objects to delete.

### Configuring the Result Type

var resultType: NSBatchDeleteRequestResultType

The type of result the request provides when it executes.

enum NSBatchDeleteRequestResultType

The types of result a batch delete request can provide when it executes.

## Relationships

### Inherits From

- NSPersistentStoreRequest

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCopying
- NSObjectProtocol

## See Also

### Data Deletion

class NSBatchDeleteResult

An object that describes the result of a batch delete request.

