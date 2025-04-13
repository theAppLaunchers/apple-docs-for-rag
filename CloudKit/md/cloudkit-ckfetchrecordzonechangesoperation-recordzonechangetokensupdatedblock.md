

- CloudKit
- CKFetchRecordZoneChangesOperation
-  recordZoneChangeTokensUpdatedBlock 

Instance Property

# recordZoneChangeTokensUpdatedBlock

The closure to execute when the change token updates.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.12+tvOS 10.0+visionOS 1.0+watchOS 3.0+

``` source
var recordZoneChangeTokensUpdatedBlock: ((CKRecordZone.ID, CKServerChangeToken?, Data?) -> Void)? { get set }
```

## Discussion

The closure returns no value and takes the following parameters:

- The record zone’s ID.

- The new change token from the server. You can store this token locally and use it during subsequent fetch operations to limit the results to records that change after this operation executes.

- The most recent client change token from the device. If the change token isn’t the most recent change token you provided, the server might not have received the associated changes.

The operation executes this closure once for each record zone. Each time the closure executes, it executes serially with respect to the other blocks of the operation.

Set this property before you execute the operation or submit it to a queue.

## See Also

### Processing the Zone Change Operation Results

var recordChangedBlock: ((CKRecord) -> Void)?

The closure to execute with the contents of a changed record.

Deprecated

var recordWithIDWasDeletedBlock: ((CKRecord.ID, CKRecord.RecordType) -> Void)?

The closure to execute when a record no longer exists.

var recordZoneFetchCompletionBlock: ((CKRecordZone.ID, CKServerChangeToken?, Data?, Bool, (any Error)?) -> Void)?

The closure to execute when a record zone’s fetch finishes.

Deprecated

var fetchRecordZoneChangesCompletionBlock: (((any Error)?) -> Void)?

The closure to execute when the operation finishes.

Deprecated

