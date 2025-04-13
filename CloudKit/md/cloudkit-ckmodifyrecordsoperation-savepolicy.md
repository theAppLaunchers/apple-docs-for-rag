

- CloudKit
- CKModifyRecordsOperation
-  savePolicy 

Instance Property

# savePolicy

The policy to use when saving changes to records.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOSvisionOS 1.0+watchOS 3.0+

``` source
var savePolicy: CKModifyRecordsOperation.RecordSavePolicy { get set }
```

## Discussion

The server uses this property to determine how to proceed when saving record changes. The exact behavior depends on the policy you choose:

- Use CKModifyRecordsOperation.RecordSavePolicy.ifServerRecordUnchanged to only save a record when the change tag of the local copy matches that of the server’s copy. If the server record’s change tag is more recent, CloudKit discards the save and returns a CKError.Code.serverRecordChanged error.

- Use CKModifyRecordsOperation.RecordSavePolicy.changedKeys to save only the fields of the record that contain changes. The server doesn’t compare record change tags when using this policy.

- Use CKModifyRecordsOperation.RecordSavePolicy.allKeys to save every field of the record, even those without changes. The server doesn’t compare record change tags when using this policy.

If you change the property’s value, do so before you execute the operation or submit the operation to a queue. The default value is CKModifyRecordsOperation.RecordSavePolicy.ifServerRecordUnchanged.

## See Also

### Configuring the Modify Record Operation

var recordsToSave: [CKRecord]?

The records to save to the database.

var recordIDsToDelete: [CKRecord.ID]?

The IDs of the records to delete permanently from the database.

var clientChangeTokenData: Data?

A token that tracks local changes to records.

var isAtomic: Bool

A Boolean value that indicates whether the entire operation fails when CloudKit can’t update one or more records in a record zone.

enum RecordSavePolicy

Constants that indicate which policy to apply when saving records.

