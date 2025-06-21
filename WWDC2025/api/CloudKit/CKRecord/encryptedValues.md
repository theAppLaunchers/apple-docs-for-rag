*   [CloudKit](/documentation/cloudkit)
*   [CKRecord](/documentation/cloudkit/ckrecord)
*   encryptedValues

Instance Property

# encryptedValues

An object that manages the record’s encrypted key-value pairs.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
@NSCopying
var encryptedValues: any [`CKRecordKeyValueSetting`](/documentation/cloudkit/ckrecordkeyvaluesetting) & [`Sendable`](/documentation/Swift/Sendable) { get }
```

```
```
```
```
```
```
```

## [Mentioned in](/documentation/CloudKit/CKRecord/encryptedValues#mentions)

[

Encrypting User Data](/documentation/cloudkit/encrypting-user-data)

## [Discussion](/documentation/CloudKit/CKRecord/encryptedValues#Discussion)

Use the object this property returns to read and write encrypted key-value pairs that you store on the record. You can encrypt values of any data type that CloudKit supports, except [`CKAsset`](/documentation/cloudkit/ckasset), which is encrypted by default, and [`CKRecord.Reference`](/documentation/cloudkit/ckrecord/reference), which isn’t encrypted so it remains available for server-side use. Only encrypt new fields. CloudKit doesn’t allow encryption on fields that already exist in your app’s schema, or on records that you store in the public database.

Note

CloudKit doesn’t support indexes on encrypted fields. Don’t include encrypted fields in your predicate or sort descriptors when fetching records with [`CKQuery`](/documentation/cloudkit/ckquery) and [`CKQueryOperation`](/documentation/cloudkit/ckqueryoperation).

CloudKit encrypts the fields’ values on-device before saving them to iCloud, and decrypts the values only after fetching them from the server. When you enable Advanced Data Protection, the encryption keys are available exclusively to the record’s owner and, if the user shares the record, that share’s participants.

The following example shows how to use `encryptedValues` to encrypt and decrypt a string value:

```swift
```swift
```swift
```swift
```swift
```swift
let record = CKRecord(recordType: "Property")
```
```
// Encrypt the name of the property's owner.
record.encryptedValues["ownerName"] = "Maria Ruiz"
// Decrypt the name of the property's owner, using the
// appropriate data type, and assign it to a local variable.
```swift
```swift
var clientName = record.encryptedValues["ownerName"] as? NSString
```
```
```
```
```
```