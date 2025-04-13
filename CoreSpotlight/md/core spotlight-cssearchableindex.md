

- Core Spotlight
-  CSSearchableIndex 

Class

# CSSearchableIndex

An on-device index for your app’s searchable content.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+visionOS 1.0+

``` source
class CSSearchableIndex
```

## Mentioned in 

Adding your app’s content to Spotlight indexes

## Overview

A `CSSearchableIndex` object manages an on-device index for your app’s searchable content. To make your app’s content searchable, package it in one or more CSSearchableItem objects and add them to the index. You can create as many searchable indexes as you need to manage your content, and you can apply different levels of encryption to protect the content in each index. When you execute a query, Core Spotlight searches your app’s indexes for the requested information and returns the results to your code.

Note

If your app creates NSUserActivity objects, set the isEligibleForSearch property of those objects to `true` to ensure they appear in search results.

Put your content into a custom `CSSearchableIndex` that you create. Custom indexes support batch operations and additional levels of data protection. Place sensitive personal information in protected indexes to encrypt that content, and prevent its disclosure without proper authorization from the owner of the device. Although you can put content into the default index, you can’t encrypt the content in that index or perform batch operations to add content to it.

When adding large amounts of data to the index, consider adding it in batches to minimize risk. Batch-based updates make it easier to handle errors that might occur during the indexing process. For each batch, you provide client-state information to identify the current batch. If your app or extension crashes while a batch operation is in progress, you can use that state information to determine where to start indexing again later.

Modify custom `CSSearchableIndex` objects only on one thread or task at a time. It’s a programming error to access a custom index from multiple threads simultaneously. When performing batch updates on an index, start each new batch operation only after calling the endBatch(withClientState:completionHandler:) or endIndexBatch(expectedClientState:newClientState:completionHandler:) method of the previous batch operation.

## Topics

### Creating an index

class func `default`() -> Self

Returns the default on-device index.

init(name: String)

Returns an on-device index with the specified name.

init(name: String, protectionClass: FileProtectionType?)

Returns an on-device index with the specified name and data protection class.

### Determining if indexing is available

class func isIndexingAvailable() -> Bool

Returns a Boolean value that indicates whether indexing is available on the current device.

### Responding to index-related changes

protocol CSSearchableIndexDelegate

A protocol that defines methods a delegate object or app extension uses to handle communication from the on-device index.

var indexDelegate: (any CSSearchableIndexDelegate)?

The delegate object that can handle index-management tasks.

### Managing items in an index

func indexSearchableItems([CSSearchableItem], completionHandler: (((any Error)?) -> Void)?)

Adds or updates items in the index.

func deleteAllSearchableItems(completionHandler: (((any Error)?) -> Void)?)

Deletes all searchable items from the index.

func deleteSearchableItems(withDomainIdentifiers: [String], completionHandler: (((any Error)?) -> Void)?)

Removes from the index all searchable items associated with the specified domain.

func deleteSearchableItems(withIdentifiers: [String], completionHandler: (((any Error)?) -> Void)?)

Removes from the index all items with the specified identifiers.

### Batching index updates

func beginBatch()

Begins a batch of updates to an index.

func endBatch(withClientState: Data, completionHandler: (((any Error)?) -> Void)?)

Ends a batch of index updates and stores the specified state information.

func endIndexBatch(expectedClientState: Data?, newClientState: Data, completionHandler: (((any Error)?) -> Void)?)

Ends a batch of index updates and stores the specified state information.

func fetchLastClientState(completionHandler: (Data?, (any Error)?) -> Void)

Fetches the app’s most recent client state information asynchronously.

### Handling drag and drop content

func fetchData(forBundleIdentifier: String, itemIdentifier: String, contentType: UTType, completionHandler: (Data?, (any Error)?) -> Void)

Fetches data from an external provider.

### Instance Methods

func deleteAppEntities&lt;Entity>(identifiedBy: [Entity.ID], ofType: Entity.Type) async throws

Deletes specific app entities from the system’s index.

func deleteAppEntities&lt;Entity>(ofType: Entity.Type) async throws

Deletes all app entities of the given type from the system indices.

func indexAppEntities([some IndexedEntity], priority: Int) async throws

Indexes the provided entities into the system.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol

## See Also

### Indexes

protocol CSSearchableIndexDelegate

A protocol that defines methods a delegate object or app extension uses to handle communication from the on-device index.

