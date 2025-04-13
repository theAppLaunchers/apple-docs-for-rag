

- CloudKit
- CKRecord
-  CKRecord.Reference 

Class

# CKRecord.Reference

A relationship between two records in a record zone.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOSvisionOS 1.0+watchOS 3.0+

``` source
class Reference
```

## Mentioned in 

Encrypting User Data

Designing and Creating a CloudKit Database

## Overview

A `CKReference` object creates a many-to-one relationship between records in your database. Each reference object stores information about the one record that is the target of the reference. You then save the reference object in the fields of one or more records to create a link from those records to the target. Both records must be in the same zone of the same database.

References create a stronger relationship between records than just saving the ID of a record as a string. Specifically, you can use references to create an ownership model between two records. When the reference object’s action is CKRecord.ReferenceAction.deleteSelf, the target of the reference—that is, the record in the reference’s recordID property—becomes the owner of the source record. Deleting the target (owner) record deletes all its source records. The deletion of any owned records can trigger further deletions if those records are the owners of other records. If a record contains two or more `CKReference` objects with an action of CKRecord.ReferenceAction.deleteSelf, CloudKit deletes the record when it deletes any of the objects it references.

Note

It is permissible to create circular owning references for a set of records.

To save multiple records that contain references between them, save the target records first or save all the records in one batch operation using CKModifyRecordsOperation.

### Interacting with Reference Objects

You use reference objects to create strong links between two records and to search for related fields. When you create new records, you create reference objects and assign them to fields of your records. The only other time you create reference objects is when you build a search predicate to search for related records.

#### Linking to Another Record

To link records together and create a strong relationship between them, create a new `CKReference` object, initialize it with the owner record, and assign that reference object to a field of the owned record. When you design the relationships among your own records, make the owner the more important of two related records. The owner record rarely depends on any records that point to it. The owner record is also the one that you typically fetch first from the database.

Important

There is a hard limit to the number of references with a CKRecord.ReferenceAction.deleteSelf action that any one record can have. This limit is 750 references, and any attempt to exceed it results in an error from the server.

The figure below shows an example of a relationship between a to-do list record and a set of item records that represent individual items to complete. The to-do list is the primary record, or owner, in the relationship because it represents the entire to-do list, including all items on the list. As a result, each item record has a field that contains a `CKReference` object that points to the owning to-do list record.

The following code sample shows how to create the reference object for each item record and configure it to point at the list record:

- Swift
- Objective-C

```
itemRecord["owningList"] = CKReference(record: listRecord, action: .deleteSelf)
```

```
CKReference* ref = [[CKReference alloc] initWithRecord:listRecord action:CKReferenceActionDeleteSelf];
itemRecord[@"owningList"] = ref;
```

An ownership type of organization is useful even if one object doesn’t explicitly own another. Ownership helps establish the relationships between records and how you search for them in the database. Ownership doesn’t require the deletion of the owned records when you delete their owner record. You can prevent such deletions by specifying the CKRecord.ReferenceAction.none action when you create a `CKReference` object.

Note

When you’re creating a `CKReference` between two objects and you have both objects in memory, be sure to fetch the object on the receiving end of the relationship. This is due to the creation of the `CKReference` between the two objects altering the recordChangeTag of the receiving object on the server.

#### Searching for Related Records

When you want to find records for a single owner object, you create a `CKReference` object and use it to build your search predicate. When you use reference objects in search predicates, the search code looks only at the ID value in the reference object. It matches the ID in records of the specified type with the ID you provide in the `CKReference` object.

The code sample below shows how to use a reference object to construct a query for the records in the figure above. The `listID` variable is a placeholder for the record ID of the list with the items you want to retrieve. The predicate tells the query object to search the `owningList` field of the target records and compare the reference object there with the one in the `recordToMatch` variable. Executing the query operation object returns the matching records asynchronously to the completion block you provide.

- Swift
- Objective-C

```
// Match item records with an owningList field that points to the specified list record.
let listID = listRecord.recordID
let recordToMatch = CKReference(recordID: listID, action: .deleteSelf)
let predicate = NSPredicate(format: "owningList == %@", recordToMatch)
// Create the query object.
let query = CKQuery(recordType: "Item", predicate: predicate)
let queryOp = CKQueryOperation(query: query)
queryOp.queryCompletionBlock = { (cursor, error) in
    // Process the results…
}
// Add the CKQueryOperation to a queue to execute it and process the results asynchronously.
```

```
// Match item records with an owningList field that points to the specified list record.
CKReference* recordToMatch = [[CKReference alloc] initWithRecordID:listID
                                                            action:CKReferenceActionDeleteSelf];
NSPredicate* predicate = [NSPredicate predicateWithFormat:@"owningList == %@", recordToMatch];
// Create the query object.
CKQuery* query = [[CKQuery alloc] initWithRecordType:@"Item" predicate:predicate];
CKQueryOperation *queryOp = [[CKQueryOperation alloc] initWithQuery:query];
[queryOp setQueryCompletionBlock:^(CKQueryCursor *nextCursor, NSError *error) {
    // Process the results…
}];
// Add the CKQueryOperation to a queue to execute it and process the results asynchronously.
```

## Topics

### Creating a Reference

init(recordID: CKRecord.ID, action: CKRecord.ReferenceAction)

Creates a reference object that points to the record with the specified ID.

convenience init(record: CKRecord, action: CKRecord.ReferenceAction)

Creates a reference object that points to the specified record object.

typealias Action

A type that represents additional actions that occur when deleting references.

### Getting the Reference Attributes

var action: CKRecord.ReferenceAction

The ownership behavior for the records.

var recordID: CKRecord.ID

The ID of the referenced record.

enum ReferenceAction

Constants that indicate the behavior when deleting a referenced record.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CKRecordValueProtocol
- CVarArg
- Copyable
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCoding
- NSCopying
- NSObjectProtocol
- NSSecureCoding
- Sendable

## See Also

### Schemas

Designing and Creating a CloudKit Database

Create a schema to store your app’s objects as records in iCloud using CloudKit.

Managing iCloud Containers with CloudKit Database App

Inspect and modify the schema and data for your app’s iCloud container.

class CKRecordZone

A database partition that contains related records.

class CKRecord

A collection of key-value pairs that store your app’s data.

class CKAsset

An external file that belongs to a record.

Integrating a Text-Based Schema into Your Workflow

Define and update your schema with the CloudKit Schema Language.

