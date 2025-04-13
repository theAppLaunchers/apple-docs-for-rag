

- CloudKit
- CKError
-  serverRecordChanged 

Type Property

# serverRecordChanged

An error that occurs when CloudKit rejects a record because the server’s version is different.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOSvisionOS 1.0+watchOS 3.0+

``` source
static var serverRecordChanged: CKError.Code { get }
```

## Discussion

This error indicates that the server’s version of the record is newer than the local version the client’s trying to save. Your app needs to handle this error, resolve any conflicts in the record, and attempt another save of the record, if necessary.

CloudKit provides your app with three copies of the record in this error’s `userInfo` dictionary to assist with comparing and merging the changes:

- CKRecordChangedErrorClientRecordKey: The local record that the client’s trying to save.

- CKRecordChangedErrorServerRecordKey: The record that exists on the server.

- CKRecordChangedErrorAncestorRecordKey: The original version of the record.

When a conflict occurs, your app needs to merge all changes into the record for the CKRecordChangedErrorServerRecordKey key and attempt a new save using that record. Merging into either of the other two copies of the record results in another conflict error because those records have the old record change tag.

## See Also

### Getting Error Codes

static var accountTemporarilyUnavailable: CKError.Code

An error that occurs when the user’s iCloud account is temporarily unavailable.

static var alreadyShared: CKError.Code

An error that occurs when CloudKit attempts to share a record with an existing share.

static var assetFileModified: CKError.Code

An error that occurs when the system modifies an asset while saving it.

static var assetFileNotFound: CKError.Code

An error that occurs when the system can’t find the specified asset.

static var assetNotAvailable: CKError.Code

An error that occurs when the system can’t access the specified asset.

static var badContainer: CKError.Code

An error that occurs when you use an unknown or unauthorized container.

static var badDatabase: CKError.Code

An error that occurs when the operation can’t complete for the specified database.

static var batchRequestFailed: CKError.Code

An error that occurs when the system rejects the entire batch of changes.

static var changeTokenExpired: CKError.Code

An error that occurs when the change token expires.

static var constraintViolation: CKError.Code

An error that occurs when the server rejects the request because of a unique constraint violation.

static var incompatibleVersion: CKError.Code

An error that occurs when the current app version is older than the oldest allowed version.

static var internalError: CKError.Code

A nonrecoverable error that CloudKit encounters.

static var invalidArguments: CKError.Code

An error that occurs when the request contains invalid information.

static var limitExceeded: CKError.Code

An error that occurs when a request’s size exceeds the limit.

static var managedAccountRestricted: CKError.Code

An error that occurs when CloudKit rejects a request due to a managed-account restriction.

