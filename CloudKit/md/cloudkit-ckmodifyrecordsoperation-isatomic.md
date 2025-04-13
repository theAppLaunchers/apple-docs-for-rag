

- CloudKit
- CKModifyRecordsOperation
-  isAtomic 

Instance Property

# isAtomic

A Boolean value that indicates whether the entire operation fails when CloudKit can’t update one or more records in a record zone.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOSvisionOS 1.0+watchOS 3.0+

``` source
var isAtomic: Bool { get set }
```

## Discussion

Modifying records atomically prevents you from updating your data in a way that would leave it in an inconsistent state. You use atomic updates when you want to write multiple records to the same record zone. If there’s a failure to modify any of the records in a zone, CloudKit doesn’t change the other records in that same zone. The record zone must have the atomic capability for this behavior to apply. If a record zone doesn’t support the atomic capability, setting this property has no effect.

The default value of this property is true, which causes all modifications within a single record zone to occur atomically. If your operation contains records in multiple record zones, a failure in one zone doesn’t prevent modifications to records in a different zone. Changing the value of this property to false causes CloudKit to modify records individually, regardless of whether the record zone supports atomic modifications.

## See Also

### Configuring the Modify Record Operation

var recordsToSave: [CKRecord]?

The records to save to the database.

var recordIDsToDelete: [CKRecord.ID]?

The IDs of the records to delete permanently from the database.

var clientChangeTokenData: Data?

A token that tracks local changes to records.

var savePolicy: CKModifyRecordsOperation.RecordSavePolicy

The policy to use when saving changes to records.

enum RecordSavePolicy

Constants that indicate which policy to apply when saving records.

