

- Core Data
-  NSPersistentStore 

Class

# NSPersistentStore

The abstract base class for all Core Data persistent stores.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.1+macOS 10.5+tvOSvisionOS 1.0+watchOS 2.0+

``` source
class NSPersistentStore
```

## Overview

Core Data provides four store types—SQLite, Binary, XML, and In-Memory (the XML store is not available on iOS); these are described in Persistent Store Features. Core Data also provides subclasses of `NSPersistentStore` that you can use to define your own store types: NSAtomicStore and NSIncrementalStore. The Binary and XML stores are examples of atomic stores that inherit functionality from `NSAtomicStore`.

### Subclassing Notes

You should not subclass `NSPersistentStore` directly. Core Data only supports subclassing of NSAtomicStore and NSIncrementalStore.

The designated initializer is init(persistentStoreCoordinator:configurationName:at:options:). When you implement the initializer, you must ensure you load metadata during initialization and set it using metadata.

You must override these methods:

- type

- metadata

- metadataForPersistentStore(with:)

- setMetadata(_:forPersistentStoreAt:)

## Topics

### Creating a Persistent Store

init(persistentStoreCoordinator: NSPersistentStoreCoordinator?, configurationName: String?, at: URL, options: [AnyHashable : Any]?)

Returns a store initialized with the given arguments.

### Getting Store Configuration

var configurationName: String

The name of the managed object model configuration that creates the persistent store.

var options: [AnyHashable : Any]?

The options that Core Data uses to create the store.

var persistentStoreCoordinator: NSPersistentStoreCoordinator?

The persistent store coordinator that loads the persistent store.

var type: String

The type string of the persistent store.

struct StoreType

The types of persistent stores that Core Data supports.

Persistent Store Types

Persist data through the available store types.

### Managing Store Attributes

var identifier: String!

The unique identifier for the persistent store.

var isReadOnly: Bool

A Boolean value that indicates whether the persistent store is read-only.

var url: URL?

The URL for the persistent store.

### Managing Store Metadata

class func metadataForPersistentStore(with: URL) throws -> [String : Any]

Returns the metadata from the persistent store at the given URL.

class func setMetadata([String : Any]?, forPersistentStoreAt: URL) throws

Sets the metadata for the store at a given URL.

func loadMetadata() throws

Instructs the persistent store to load its metadata.

var metadata: [String : Any]!

The metadata for the persistent store.

### Responding to the Store Life Cycle

func didAdd(to: NSPersistentStoreCoordinator)

Invoked after the persistent store has been added to the persistent store coordinator.

func willRemove(from: NSPersistentStoreCoordinator?)

Invoked before the persistent store is removed from the persistent store coordinator.

### Integrating with Spotlight

var coreSpotlightExporter: NSCoreDataCoreSpotlightDelegate

The spotlight exporter associated with this persistent store.

### Providing a Migration Manager

class func migrationManagerClass() -> AnyClass

Returns the migration manager class for this store class.

## Relationships

### Inherits From

- NSObject

### Inherited By

- NSAtomicStore
- NSIncrementalStore

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol

## See Also

### Store Coordination

class NSPersistentStoreCoordinator

An object that enables an app’s contexts and the underlying persistent stores to work together.

class NSPersistentStoreDescription

A description object used to create and load a persistent store.

class NSPersistentStoreRequest

Criteria used to retrieve data from or save data to a persistent store.

class NSPersistentStoreResult

The abstract base class for results returned from a persistent store coordinator.

class NSPersistentStoreAsynchronousResult

A concrete class used to represent the results of an asynchronous request.

class NSSaveChangesRequest

An encapsulation of a collection of changes to be made by an object store in response to a save operation on a managed object context.

class NSAtomicStore

An abstract superclass that you subclass to create a Core Data atomic store.

class NSAtomicStoreCacheNode

A concrete class that you use to represent basic nodes in a Core Data atomic store.

class NSIncrementalStore

An abstract superclass defining the API through which Core Data communicates with a store.

class NSIncrementalStoreNode

A concrete class used to represent basic nodes in a Core Data incremental store.

