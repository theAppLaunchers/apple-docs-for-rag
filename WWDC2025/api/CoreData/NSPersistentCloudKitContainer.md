*   [Core Data](/documentation/coredata)
*   NSPersistentCloudKitContainer

Class

# NSPersistentCloudKitContainer

A container that encapsulates the Core Data stack in your app, and mirrors select persistent stores to a CloudKit private database.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class NSPersistentCloudKitContainer
```
```
```
```
```
```
```
```

## [Mentioned in](/documentation/CoreData/NSPersistentCloudKitContainer#mentions)

[

Setting Up Core Data with CloudKit](/documentation/coredata/setting-up-core-data-with-cloudkit)

[

Reading CloudKit Records for Core Data](/documentation/coredata/reading-cloudkit-records-for-core-data)

[

Mirroring a Core Data store with CloudKit](/documentation/coredata/mirroring-a-core-data-store-with-cloudkit)

## [Overview](/documentation/CoreData/NSPersistentCloudKitContainer#overview)

[`NSPersistentCloudKitContainer`](/documentation/coredata/nspersistentcloudkitcontainer) is a subclass of [`NSPersistentContainer`](/documentation/coredata/nspersistentcontainer) capable of managing both CloudKit-backed and noncloud stores.

By default, [`NSPersistentCloudKitContainer`](/documentation/coredata/nspersistentcloudkitcontainer) contains a single store description, which Core Data assigns to the first CloudKit container identifier in an app’s entitlements. Use [`NSPersistentCloudKitContainerOptions`](/documentation/coredata/nspersistentcloudkitcontaineroptions) to customize this behavior or create additional store descriptions with backing by different containers.

For more information about setting up multiple stores, see [Setting Up Core Data with CloudKit](/documentation/coredata/setting-up-core-data-with-cloudkit).

## [Topics](/documentation/CoreData/NSPersistentCloudKitContainer#topics)

### [Checking Permissions](/documentation/CoreData/NSPersistentCloudKitContainer#Checking-Permissions)

```swift
```swift
```swift
```swift
func canUpdateRecord(forManagedObjectWith: NSManagedObjectID) -> Bool
```
```

Returns a Boolean value that indicates whether the user can modify the managed object’s underlying CloudKit record.
```
```swift
```swift
```swift
func canDeleteRecord(forManagedObjectWith: NSManagedObjectID) -> Bool
```
```

Returns a Boolean value that indicates whether the user can delete the managed object’s underlying CloudKit record.
```
```swift
```swift
```swift
func canModifyManagedObjects(in: NSPersistentStore) -> Bool
```
```

Returns a Boolean value that indicates whether the user can modify the specified persistent store.
```
```

### [Sharing Objects](/documentation/CoreData/NSPersistentCloudKitContainer#Sharing-Objects)

[

Accepting Share Invitations in a SwiftUI App](/documentation/coredata/accepting-share-invitations-in-a-swiftui-app)

Adapt your app to use UIKit’s application and scene delegates so it can process CloudKit share invitations.

### [Promoting Your Schema](/documentation/CoreData/NSPersistentCloudKitContainer#Promoting-Your-Schema)

```swift
```swift
```swift
```swift
func initializeCloudKitSchema(options: NSPersistentCloudKitContainerSchemaInitializationOptions) throws
```
```

Creates the CloudKit schema for all stores in the container that manage a CloudKit database.
```
```swift
```swift
```swift
struct NSPersistentCloudKitContainerSchemaInitializationOptions
```
```

Options that control the behavior when promoting the container’s schema to CloudKit.
```
```

### [Monitoring Container Events](/documentation/CoreData/NSPersistentCloudKitContainer#Monitoring-Container-Events)

```swift
```swift
```swift
```swift
class Event
```
```

An object that represents activity in a persistent CloudKit container.
```
```swift
```swift
```swift
enum EventType
```
```

The type of event in a persistent CloudKit container, either setup, import, or export.
```
```swift
```swift
```swift
class NSPersistentCloudKitContainerEventRequest
```
```

A request to fetch setup, import, or export events in a persistent CloudKit container.
```
```swift
```swift
```swift
class NSPersistentCloudKitContainerEventResult
```
```

The result of a request to fetch persistent CloudKit container events.
```
```swift
```swift
```swift
class let eventChangedNotification: NSNotification.Name
```
```

A notification that contains details about an event in a persistent CloudKit container.
```
```swift
```swift
```swift
class let eventNotificationUserInfoKey: String
```
```

The user info dictionary key for the persistent CloudKit container event.
```
```

## [Relationships](/documentation/CoreData/NSPersistentCloudKitContainer#relationships)

### [Inherits From](/documentation/CoreData/NSPersistentCloudKitContainer#inherits-from)

*   [`NSPersistentContainer`](/documentation/coredata/nspersistentcontainer)

### [Conforms To](/documentation/CoreData/NSPersistentCloudKitContainer#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)

## [See Also](/documentation/CoreData/NSPersistentCloudKitContainer#see-also)

### [CloudKit mirroring](/documentation/CoreData/NSPersistentCloudKitContainer#CloudKit-mirroring)

[

Mirroring a Core Data store with CloudKit](/documentation/coredata/mirroring-a-core-data-store-with-cloudkit)

Back user interfaces with a local replica of a CloudKit private database.

[

Synchronizing a local store to the cloud](/documentation/coredata/synchronizing-a-local-store-to-the-cloud)

Share data between a user’s devices and other iCloud users.

```swift
```swift
```swift
class NSPersistentCloudKitContainerOptions
```
```

An object that customizes how a store description aligns with a CloudKit database.
```

[

Sharing Core Data objects between iCloud users](/documentation/coredata/sharing-core-data-objects-between-icloud-users)

Use Core Data and CloudKit to synchronize data between devices of an iCloud user and share data between different iCloud users.