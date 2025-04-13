

- CloudKit
-  CKFetchDatabaseChangesOperation 

Class

# CKFetchDatabaseChangesOperation

An operation that fetches database changes.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.12+tvOS 10.0+visionOS 1.0+watchOS 3.0+

``` source
class CKFetchDatabaseChangesOperation
```

## Overview

Use this operation to fetch all record zone changes in a database. This includes new record zones, changed zones — including deleted or purged zones — and zones that contain record changes. When you create the operation, you provide a server change token, which is an opaque token that represents a specific point in the database’s history. CloudKit returns only the changes that occur after that point. For your app’s first fetch, or to refetch every change in the database’s history, use `nil` instead.

Note

Only private and shared databases support this operation. If you attempt to execute this operation in the public database, CloudKit returns an error.

The operation yields new change tokens during its execution, and issues a final change token when it completes without error. The change tokens conform to NSSecureCoding and are safe to cache on-disk. This operation’s tokens aren’t compatible with CKFetchRecordZoneChangesOperation so you should segregate them in your cache. Don’t infer any behavior or order from the tokens’ contents.

When your app launches for the first time, use this operation to fetch all the database’s changes. Cache the results on-device and use CKDatabaseSubscription to subscribe to future changes. Fetch those changes on receipt of the push notifications the subscription generates. It’s not necessary to perform a fetch each time your app launches, or to schedule fetches at regular intervals.

The operation calls recordZoneWithIDChangedBlock for each zone that contains record changes. It also calls it for new and modified record zones. Store the IDs that CloudKit provides to this callback. Use those IDs with CKFetchRecordZoneChangesOperation to fetch the corresponding changes. There are similar callbacks for deleted and purged record zones.

To run the operation, add it to the corresponding database’s operation queue. The operation executes its callbacks on a private serial queue.

The following example shows how to create the operation, configure its callbacks, and execute it. For brevity, it omits the delete and purge callbacks.

```
// Create a fetch operation using the server change
// token from the previous fetch.
CKFetchDatabaseChangesOperation *operation =
    [[CKFetchDatabaseChangesOperation alloc]
     initWithPreviousServerChangeToken:token];

// Collect the IDs of the modified record zones.
operation.recordZoneWithIDChangedBlock = ^(CKRecordZoneID *recordZoneID) {
    [recordZoneIDs addObject:recordZoneID];
};

// Process any change tokens that CloudKit provides
// as the operation runs.
operation.changeTokenUpdatedBlock = ^(CKServerChangeToken *newToken) {
    tokenHandler(newToken);
};

// Store the final change token and pass the IDs of the
// modified record zones for further processing.
operation.fetchDatabaseChangesCompletionBlock =
    ^(CKServerChangeToken *newToken, BOOL more, NSError *error) {
    if (error) {
        // Handle the error.
    } else {
        tokenHandler(newToken);
        recordZonesHandler(recordZoneIDs);
    }
};

// Set an appropriate QoS and add the operation to the shared
// database's operation queue to execute it.
operation.qualityOfService = NSQualityOfServiceUtility;
[CKContainer.defaultContainer.sharedCloudDatabase addOperation:operation];
```

## Topics

### Creating an Operation

convenience init(previousServerChangeToken: CKServerChangeToken?)

Creates an operation for fetching database changes.

init()

Creates an empty fetch database changes operation.

### Configuring the Operation

var fetchAllChanges: Bool

A Boolean value that indicates whether to send repeated requests to the server.

var previousServerChangeToken: CKServerChangeToken?

The server change token.

var resultsLimit: Int

The maximum number of results that the operation fetches.

### Processing the Operation’s Results

var recordZoneWithIDChangedBlock: ((CKRecordZone.ID) -> Void)?

The closure to execute with a single record zone change.

var recordZoneWithIDWasDeletedBlock: ((CKRecordZone.ID) -> Void)?

The closure to execute when a record zone no longer exists.

var recordZoneWithIDWasDeletedDueToUserEncryptedDataResetBlock: ((CKRecordZone.ID) -> Void)?

The closure to execute when a user-invoked account reset deletes a record zone.

var recordZoneWithIDWasPurgedBlock: ((CKRecordZone.ID) -> Void)?

The closure to execute when CloudKit purges a record zone.

var changeTokenUpdatedBlock: ((CKServerChangeToken) -> Void)?

The closure to execute when the change token updates.

var fetchDatabaseChangesCompletionBlock: ((CKServerChangeToken?, Bool, (any Error)?) -> Void)?

The closure to execute when the operation finishes.

Deprecated

### Instance Properties

var fetchDatabaseChangesResultBlock: ((Result&lt;(serverChangeToken: CKServerChangeToken, moreComing: Bool), any Error>) -> Void)?

## Relationships

### Inherits From

- CKDatabaseOperation

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol
- Sendable

## See Also

### Database Changes

class CKDatabaseSubscription

A subscription that generates push notifications when CloudKit modifies records in a database.

class CKDatabaseNotification

A notification that triggers when the contents of a database change.

