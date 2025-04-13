

- CloudKit
- CKFetchDatabaseChangesOperation
-  recordZoneWithIDWasDeletedDueToUserEncryptedDataResetBlock 

Instance Property

# recordZoneWithIDWasDeletedDueToUserEncryptedDataResetBlock

The closure to execute when a user-invoked account reset deletes a record zone.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
var recordZoneWithIDWasDeletedDueToUserEncryptedDataResetBlock: ((CKRecordZone.ID) -> Void)? { get set }
```

## Discussion

The closure returns no value and takes a single parameter: the deleted record zone’s ID.

The operation executes this closure, instead of recordZoneWithIDWasDeletedBlock, after a user action causes CloudKit to delete the record zone. Reupload any locally cached data to iCloud to minimize data loss.

## See Also

### Processing the Operation’s Results

var recordZoneWithIDChangedBlock: ((CKRecordZone.ID) -> Void)?

The closure to execute with a single record zone change.

var recordZoneWithIDWasDeletedBlock: ((CKRecordZone.ID) -> Void)?

The closure to execute when a record zone no longer exists.

var recordZoneWithIDWasPurgedBlock: ((CKRecordZone.ID) -> Void)?

The closure to execute when CloudKit purges a record zone.

var changeTokenUpdatedBlock: ((CKServerChangeToken) -> Void)?

The closure to execute when the change token updates.

var fetchDatabaseChangesCompletionBlock: ((CKServerChangeToken?, Bool, (any Error)?) -> Void)?

The closure to execute when the operation finishes.

Deprecated

