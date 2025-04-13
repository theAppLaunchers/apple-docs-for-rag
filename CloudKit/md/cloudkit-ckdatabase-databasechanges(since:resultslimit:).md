

- CloudKit
- CKDatabase
-  databaseChanges(since:resultsLimit:) 

Instance Method

# databaseChanges(since:resultsLimit:)

Fetches all modified record zones and returns them to an awaiting caller.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOSwatchOS 8.0+

``` source
func databaseChanges(
    since changeToken: CKServerChangeToken?,
    resultsLimit: Int? = nil
) async throws -> (modifications: [CKDatabase.DatabaseChange.Modification], deletions: [CKDatabase.DatabaseChange.Deletion], changeToken: CKServerChangeToken, moreComing: Bool)
```

## Parameters 

`changeToken`  

The change token from the previous execution of this method. If this is your app’s first fetch, or you want to refetch every change in the database’s history, specify `nil`.

`resultsLimit`  

The maximum number of changes to return. The server may use a limit lower than this value.

## Return Value

A tuple with the following named elements:

## Discussion

`modifications`  
An array of database modifications that occur after the time that `changeToken` denotes. Each modification contains details about a modified record zone.

`deletions`  
An array of database deletions that occur after the time that `changeToken` denotes. Each deletion contains details about a deleted or purged record zone.

`changeToken`  
The change token that corresponds to the fetch results’ most recent change.

`moreComing`  
A Boolean value that indicates whether the server has additional changes for you to fetch.

## Discussion

This method fetches record zone changes in a database, which includes new record zones, changed zones — including deleted or purged zones — and zones that contain record changes. It throws an error if the request fails, such as when the network is unavailable or the device doesn’t have an active iCloud account.

Along with the fetched changes, CloudKit supplies a *change token*, which is an opaque token that denotes a specific point in the database’s history. Store this token and provide it the next time you execute this method. Change tokens conform to NSSecureCoding and are safe to cache on-disk. Don’t infer any behavior or order from a token’s contents.

For information on a more configurable way to fetch database changes, see CKFetchDatabaseChangesOperation.

## See Also

### Fetching Changes

func fetchDatabaseChanges(since: CKServerChangeToken?, resultsLimit: Int?, completionHandler: (Result&lt;(modifications: [CKDatabase.DatabaseChange.Modification], deletions: [CKDatabase.DatabaseChange.Deletion], changeToken: CKServerChangeToken, moreComing: Bool), any Error>) -> Void)

Fetches all modified record zones and delivers them to a completion handler.

enum DatabaseChange

Objects that indicate the type of database change.

func recordZoneChanges(inZoneWith: CKRecordZone.ID, since: CKServerChangeToken?, desiredKeys: [CKRecord.FieldKey]?, resultsLimit: Int?) async throws -> (modificationResultsByID: [CKRecord.ID : Result&lt;CKDatabase.RecordZoneChange.Modification, any Error>], deletions: [CKDatabase.RecordZoneChange.Deletion], changeToken: CKServerChangeToken, moreComing: Bool)

Fetches all modified records from a specific record zone and returns them to an awaiting caller.

func fetchRecordZoneChanges(inZoneWith: CKRecordZone.ID, since: CKServerChangeToken?, desiredKeys: [CKRecord.FieldKey]?, resultsLimit: Int?, completionHandler: (Result&lt;(modificationResultsByID: [CKRecord.ID : Result&lt;CKDatabase.RecordZoneChange.Modification, any Error>], deletions: [CKDatabase.RecordZoneChange.Deletion], changeToken: CKServerChangeToken, moreComing: Bool), any Error>) -> Void)

Fetches all modified records from a specific record zone and delivers them to a completion handler.

enum RecordZoneChange

Objects that indicate the type of record zone change.

