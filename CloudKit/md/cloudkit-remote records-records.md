

- CloudKit
-  Remote Records 

API Collection

# Remote Records

Use subscriptions and change tokens to efficiently manage modifications to remote records.

## Overview

CloudKit stores your records in iCloud and uses subscriptions to notify your app in real time about record changes. You then use change tokens to handle these changes efficiently. Additionally, you can improve your app’s performance and support offline use by storing records in a local cache.

When your app launches for the first time on a new device, use CKFetchDatabaseChangesOperation and CKFetchRecordZoneChangesOperation to fetch any records you need to populate your cache. Each operation expects a change token, which is an opaque token that represents a specific point in the database’s history. For the initial fetch, pass `nil` as the token to retrieve all changes in the database’s history. When the operation completes, save its change token so you can use it with your next fetch. Change tokens help reduce the amount of data CloudKit returns.

After you fetch the records, subscribe to future changes. Subscriptions run in iCloud and listen for record changes, such as record creation, modification, and deletion. Create subscriptions, as necessary, in the public database, and the user’s private and shared databases. A subscription responds to changes to a database, to a custom record zone, or to records that match a specific set of criteria. You can further scope subscriptions to an individual record type.

When the user modifies records on their device, save those changes to iCloud. In response, a subscription generates push notifications using the configuration you provide, and iCloud sends them to the user’s other devices. On receipt of a notification, fetch the changes from iCloud and update your cache. Use the change token from the previous fetch to limit the fetched records. Overwrite the token with the new one the fetch operation provides when it completes.

Note

Subscriptions belong to the users that create them. iCloud can notify several users’ devices in response to a change in the public database. This is because each user’s subscription is tracking the same set of records.

Every subscription type has a corresponding notification object that you can configure to meet your app’s needs. CloudKit supports high-priority visual notifications and medium-priority background notifications. A notification can include a limited number of fields from the changed record. You opt in to this behavior. For more information, see desiredKeys.

Because the system coalesces notifications, don’t rely on them for specific changes. Consider notifications an indication of remote changes, and use the fetch operations to reliably retrieve all changes that occur after your most recent fetch.

CloudKit supports the following subscription types:

| **Database** | Use a database subscription when you don’t know what record zones exist, such as in the shared database. Only private and shared databases support database subscriptions. For more information, see CKDatabaseSubscription. |
|----|----|
| **Record zone** | Use a record zone subscription to track changes in a custom record zone in the user’s private database. You can’t use this subscription in public or shared databases. For more information, see CKRecordZoneSubscription. |
| **Query** | Use a query subscription to track changes to records in a database that match a predicate. Only public and private databases support query subscriptions. For more information, see CKQuerySubscription. |

### Integrate Records with Your Existing Models

If you already cache your app’s model objects, you don’t need to cache CloudKit records in tandem. Instead, attach a record’s metadata to a model to associate the two. The metadata includes the record’s ID, record type, record zone ID, and change tag, as well as other information.

When you fetch a record from iCloud, update the local model object using the record’s fields. Then encode the record’s metadata, attach it to the model, and save the model to the cache. To update a record in iCloud, decode the model’s metadata and use it to create an instance of CKRecord. Set the record’s fields to the model’s values and save it to iCloud.

The following example shows how to encode a record’s metadata and store it on a custom `Product` model. It also shows how to decode the metadata and use it to create an instance of CKRecord.

```
func storeCloudRecord(_ record: CKRecord, on product: Product) {

    // Encode the record's metadata.
    let coder = NSKeyedArchiver(requiringSecureCoding: true)
    record.encodeSystemFields(with: coder)

    // Attach the encoded metadata to the 
    // model object so you can store it in
    // your local cache.
    product.recordMetadata = coder.encodedData
}

func extractCloudRecord(from product: Product) throws -> CKRecord? {
    guard let metadata = product.recordMetadata else { return nil }

    // Create an unarchiver from the record's stored metadata
    // and use it to create an instance of CKRecord.
    let coder = try NSKeyedUnarchiver(forReadingFrom: metadata)
    let record = CKRecord(coder: coder)
    coder.finishDecoding()

    // Return the record to the caller, which can update its 
    // fields using the product's properties before saving
    // it to iCloud.
    return record
}
```

## Topics

### Database Changes

class CKDatabaseSubscription

A subscription that generates push notifications when CloudKit modifies records in a database.

class CKDatabaseNotification

A notification that triggers when the contents of a database change.

class CKFetchDatabaseChangesOperation

An operation that fetches database changes.

### Record Zone Changes

class CKRecordZoneSubscription

A subscription that generates push notifications when CloudKit modifies records in a specific record zone.

class CKRecordZoneNotification

A notification that triggers when the contents of a record zone change.

class CKFetchRecordZoneChangesOperation

An operation that fetches record zone changes.

### Change Tokens

class CKServerChangeToken

An opaque token that represents a specific point in a database’s history.

### Subscription Management

class CKFetchSubscriptionsOperation

An operation for fetching subscriptions.

class CKModifySubscriptionsOperation

An operation for modifying one or more subscriptions.

### Predicate-Driven Changes

class CKQuerySubscription

A subscription that generates push notifications when CloudKit modifies records that match a predicate.

class CKQueryNotification

A notification that triggers when a record that matches the subscription’s predicate changes.

### Base Objects

class CKSubscription

An abstract base class for subscriptions.

class CKNotification

The abstract base class for CloudKit notifications.

class CKDatabaseOperation

The abstract base class for operations that act upon databases in CloudKit.

## See Also

### Records

Local Records

Manipulate records on-device and save changes to the server.

class CKSyncEngine

An object that manages the synchronization of local and remote record data.

Shared Records

Share one or more records with other iCloud users.

