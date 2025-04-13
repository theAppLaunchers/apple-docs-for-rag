

- Core Data
-  NSFetchedPropertyDescription 

Class

# NSFetchedPropertyDescription

A description object used to define which properties are fetched from Core Data.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.1+macOS 10.4+tvOSvisionOS 1.0+watchOS 2.0+

``` source
class NSFetchedPropertyDescription
```

## Overview

An example might be a iTunes playlist, if expressed as a property of a containing object. Songs don’t belong to a particular playlist, especially in the case that they’re on a remote server. The playlist may remain even after the songs have been deleted, or the remote server has become inaccessible. Note, however, that unlike a playlist a fetched property is static—it does not dynamically update itself as objects in the destination entity change.

The effect of a fetched property is similar to executing a fetch request yourself and placing the results in a transient attribute, although with the framework managing the details. In particular, a fetched property is not fetched until it is requested, and the results are then cached until the object is turned into a fault. You use refresh(_:mergeChanges:) (`NSManagedObjectContext`) to manually refresh the properties—this causes the fetch request associated with this property to be executed again when the object fault is next fired.

Unlike other relationships, which are all sets, fetched properties are represented by an ordered `NSArray` object just as if you executed the fetch request yourself. The fetch request associated with the property can have a sort ordering. The value for a fetched property of a managed object does not support `mutableArrayValueForKey:`.

### Fetch Request Variables

Fetch requests set on an fetched property have 2 special variable bindings you can use: `$FETCH_SOURCE` and `$FETCHED_PROPERTY`. The source refers to the specific managed object that has this property; the property refers to the `NSFetchedPropertyDescription` object itself (which may have a user info associated with it that you want to use).

### Editing Fetched Property Descriptions

Fetched Property descriptions are editable until they are used by an object graph manager. This allows you to create or modify them dynamically. However, once a description is used (when the managed object model to which it belongs is associated with a persistent store coordinator), it *must not* (indeed cannot) be changed. This is enforced at runtime: any attempt to mutate a model or any of its subjects after the model is associated with a persistent store coordinator causes an exception to be thrown. If you need to modify a model that is in use, create a copy, modify the copy, and then discard the objects with the old model.

## Topics

### Getting and setting the fetch request

var fetchRequest: NSFetchRequest&lt;any NSFetchRequestResult>?

The fetch request of the receiver.

## Relationships

### Inherits From

- NSPropertyDescription

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCoding
- NSCopying
- NSObjectProtocol

## See Also

### Specifying Fetch Constraints

var predicate: NSPredicate?

The predicate of the fetch request.

var fetchLimit: Int

The fetch limit of the fetch request.

var fetchOffset: Int

The fetch offset of the fetch request.

var fetchBatchSize: Int

The batch size of the objects specified in the fetch request.

var affectedStores: [NSPersistentStore]?

An array of persistent stores specified for the fetch request.

class NSFetchRequestExpression

An expression that evaluates the result of a fetch request on a managed object context.

class NSExpressionDescription

An object that describes an expression to include with a fetch request.

