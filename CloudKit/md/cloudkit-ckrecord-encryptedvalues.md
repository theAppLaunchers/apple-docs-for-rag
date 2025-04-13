

- CloudKit
- CKRecord
-  encryptedValues 

Instance Property

# encryptedValues

An object that manages the record’s encrypted key-value pairs.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
@NSCopying
var encryptedValues: any CKRecordKeyValueSetting & Sendable { get }
```

## Mentioned in 

Encrypting User Data

## Discussion

Use the object this property returns to read and write encrypted key-value pairs that you store on the record. You can encrypt values of any data type that CloudKit supports, except CKAsset, which is encrypted by default, and CKRecord.Reference, which isn’t encrypted so it remains available for server-side use. Only encrypt new fields. CloudKit doesn’t allow encryption on fields that already exist in your app’s schema, or on records that you store in the public database.

Note

CloudKit doesn’t support indexes on encrypted fields. Don’t include encrypted fields in your predicate or sort descriptors when fetching records with CKQuery and CKQueryOperation.

CloudKit encrypts the fields’ values on-device before saving them to iCloud, and decrypts the values only after fetching them from the server. When you enable Advanced Data Protection, the encryption keys are available exclusively to the record’s owner and, if the user shares the record, that share’s participants.

The following example shows how to use `encryptedValues` to encrypt and decrypt a string value:

```
let record = CKRecord(recordType: "Property")

// Encrypt the name of the property's owner.
record.encryptedValues["ownerName"] = "Maria Ruiz"

// Decrypt the name of the property's owner, using the
// appropriate data type, and assign it to a local variable.
var clientName = record.encryptedValues["ownerName"] as? NSString
```

