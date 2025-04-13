

- CloudKit
- CKQuery
-  recordType 

Instance Property

# recordType

The record type to search.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOS 9.0+visionOSwatchOS 3.0+Swift 4.2+

``` source
var recordType: CKRecord.RecordType { get }
```

## Discussion

A query’s results include only records of the specified type. The record type is an app-specific string that you use to distinguish among the records of your app. The records of a particular type all represent different instances of the same information. For example, an employee record type might store the employee’s name, phone number, and a reference to the employee’s manager.

## See Also

### Accessing the Query Parameters

var predicate: NSPredicate

The predicate to use for matching records.

var sortDescriptors: [NSSortDescriptor]?

The sort descriptors for organizing the query’s results.

