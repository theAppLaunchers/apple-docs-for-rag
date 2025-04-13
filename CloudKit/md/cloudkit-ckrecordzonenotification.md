

- CloudKit
-  CKRecordZoneNotification 

Class

# CKRecordZoneNotification

A notification that triggers when the contents of a record zone change.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOSvisionOS 1.0+watchOS 3.0+

``` source
class CKRecordZoneNotification
```

## Overview

A record zone subscription executes when a user, or in certain scenarios, CloudKit, modifies a record in that zone, for example, when a field’s value changes in a record. When CloudKit registers the change, it sends push notifications to the user’s devices to inform your app about the change. You can then fetch the changes and cache them on-device. When appropriate, CloudKit excludes the device where the change originates.

You configure a subscription’s notifications by setting it’s notificationInfo property. Do this before you save it to the server. A subscription generates either high-priority or medium-priority push notifications. CloudKit delivers medium-priority notifications to your app in the background. High-priority notifications are visual and the system displays them to the user. Visual notifications need the user’s permission. For more information, see Asking permission to use notifications.

A subscription uses CKSubscription.NotificationInfo to configure its notifications. For background delivery, set only its shouldSendContentAvailable property to true. If you set any other property, CloudKit treats the notification as high-priority.

Note

To receive silent push notifications, add the Background Modes capability to your Xcode project and select the “Background fetch” and “Remote notifications” options.

Don’t rely on push notifications for specific changes to records because the system can coalesce them. CloudKit can omit data to keep the notification’s payload size under the APNs size limit. Consider notifications an indication of remote changes. Use databaseScope to determine which database contains the changed record zone, and recordZoneID to determine which zone contains changed records. You can then fetch just those changes using CKFetchRecordZoneChangesOperation. A notification’s isPruned property is true if CloudKit omits data.

You don’t instantiate this class. Instead, implement application(_:didReceiveRemoteNotification:fetchCompletionHandler:) in your app delegate. Initialize CKNotification with the `userInfo` dictionary that CloudKit passes to the method. This returns an instance of the appropriate subclass. Use the notificationType property to determine the type. Then cast to that type to access type-specific properties and methods.

## Topics

### Getting the Record Zone ID

var recordZoneID: CKRecordZone.ID?

The ID of the record zone that has changes.

### Getting the Database Scope

var databaseScope: CKDatabase.Scope

The type of database for the record zone.

## Relationships

### Inherits From

- CKNotification

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol
- Sendable

## See Also

### Record Zone Changes

class CKRecordZoneSubscription

A subscription that generates push notifications when CloudKit modifies records in a specific record zone.

class CKFetchRecordZoneChangesOperation

An operation that fetches record zone changes.

