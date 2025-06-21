*   [Core Data](/documentation/coredata)
*   NSCoreDataCoreSpotlightDelegate

Class

# NSCoreDataCoreSpotlightDelegate

A set of methods that enable integration with Core Spotlight.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.13+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class NSCoreDataCoreSpotlightDelegate
```
```
```
```
```
```
```
```

## [Overview](/documentation/CoreData/NSCoreDataCoreSpotlightDelegate#overview)

Note

Core Spotlight integration is only available for persistent stores that have a store type of [`sqlite`](/documentation/coredata/nspersistentstore/storetype/sqlite), and which use persistent history tracking. For more information, see [Consuming relevant store changes](/documentation/coredata/consuming-relevant-store-changes).

## [Topics](/documentation/CoreData/NSCoreDataCoreSpotlightDelegate#topics)

### [Creating a Core Spotlight Delegate](/documentation/CoreData/NSCoreDataCoreSpotlightDelegate#Creating-a-Core-Spotlight-Delegate)

[`init(forStoreWith: NSPersistentStoreDescription, coordinator: NSPersistentStoreCoordinator)`](/documentation/coredata/nscoredatacorespotlightdelegate/init\(forstorewith:coordinator:\))

Creates a Core Spotlight delegate with the specified store description and coordinator.

[`convenience init(forStoreWith: NSPersistentStoreDescription, model: NSManagedObjectModel)`](/documentation/coredata/nscoredatacorespotlightdelegate/init\(forstorewith:model:\))

Creates a Core Spotlight delegate with the specified store description and managed object model.

Deprecated

### [Configuring the Index](/documentation/CoreData/NSCoreDataCoreSpotlightDelegate#Configuring-the-Index)

```swift
```swift
```swift
```swift
var isIndexingEnabled: Bool
```
```

A Boolean value that indicates whether Core Data is currently updating the Core Spotlight index with the persistent store’s entities.
```
```swift
```swift
```swift
func domainIdentifier() -> String
```
```

Returns the domain identifier.
```
```swift
```swift
```swift
func indexName() -> String?
```
```

Returns the index’s name.
```
```

### [Managing the Index](/documentation/CoreData/NSCoreDataCoreSpotlightDelegate#Managing-the-Index)

```swift
```swift
```swift
```swift
func attributeSet(for: NSManagedObject) -> CSSearchableItemAttributeSet?
```
```

Returns the searchable attributes for the specified managed object.
```
```swift
```swift
```swift
func deleteSpotlightIndex(completionHandler: ((any Error)?) -> Void)
```
```

Deletes all searchable items from the configured index.
```
```swift
```swift
```swift
func startSpotlightIndexing()
```
```

Starts the indexing of the store’s entities.
```
```swift
```swift
```swift
func stopSpotlightIndexing()
```
```

Stops the indexing of the store’s entities.
```
```

### [Updating the Index](/documentation/CoreData/NSCoreDataCoreSpotlightDelegate#Updating-the-Index)

[`static let indexDidUpdateNotification: Notification.Name`](/documentation/coredata/nscoredatacorespotlightdelegate/indexdidupdatenotification)

The notification the delegate posts after Spotlight updates the index.

```swift
```swift
```swift
func searchableIndex(CSSearchableIndex, reindexAllSearchableItemsWithAcknowledgementHandler: () -> Void)
```
```

Reindexes all searchable items and clears any local state.
```
```swift
```swift
```swift
func searchableIndex(CSSearchableIndex, reindexSearchableItemsWithIdentifiers: [String], acknowledgementHandler: () -> Void)
```
```

Reindexes the searchable items for the specified identifiers.
```

## [Relationships](/documentation/CoreData/NSCoreDataCoreSpotlightDelegate#relationships)

### [Inherits From](/documentation/CoreData/NSCoreDataCoreSpotlightDelegate#inherits-from)

*   [`NSObject`](/documentation/ObjectiveC/NSObject-swift.class)

### [Conforms To](/documentation/CoreData/NSCoreDataCoreSpotlightDelegate#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)

## [See Also](/documentation/CoreData/NSCoreDataCoreSpotlightDelegate#see-also)

### [Integrating with Spotlight](/documentation/CoreData/NSCoreDataCoreSpotlightDelegate#Integrating-with-Spotlight)

```swift
```swift
```swift
```swift
let NSCoreDataCoreSpotlightExporter: String
```
```

The key you use to specify your Core Spotlight delegate.
```

[

API Reference

Spotlight record keys](/documentation/coredata/spotlight-record-keys)

The keys for the values that exist in Spotlight’s external record files.

[

Showcase App Data in Spotlight](/documentation/coredata/showcase-app-data-in-spotlight)

Index app data so users can find it by using Spotlight search.
```