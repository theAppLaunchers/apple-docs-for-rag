

- CloudKit
- CKDatabase
-  fetch(withQuery:inZoneWith:desiredKeys:resultsLimit:completionHandler:) 

Instance Method

# fetch(withQuery:inZoneWith:desiredKeys:resultsLimit:completionHandler:)

Searches for records that match a predicate and delivers them to a completion handler.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOSwatchOS 8.0+

``` source
@preconcurrency
func fetch(
    withQuery query: CKQuery,
    inZoneWith zoneID: CKRecordZone.ID? = nil,
    desiredKeys: [CKRecord.FieldKey]? = nil,
    resultsLimit: Int = CKQueryOperation.maximumResults,
    completionHandler: @escaping (Result)], queryCursor: CKQueryOperation.Cursor?), any Error>) -> Void
)
```

## Parameters 

`query`  

The query that contains the search parameters. For more information, see CKQuery.

`zoneID`  

The identifier of the record zone to search. If you’re searching a shared database, provide a record zone identifier; otherwise, you can specify `nil` to search all record zones in the database.

`desiredKeys`  

The fields to include on each fetched record. To include all fields, specify `nil`; to fetch only system fields, specify an empty array.

`resultsLimit`  

The maximum number of records to return in a single set of results.

`completionHandler`  

The closure to execute with the search results.

## Discussion

The completion handler takes a single Result parameter that contains either a tuple, or an error if the request fails. For example, when the network is unavailable or the device doesn’t have an active iCloud account.

When present, the tuple contains the following named elements:

`matchResults`  
An array of tuples. Each tuple includes a record identifier and a Result that contains either the corresponding matched record, or an error that describes why CloudKit can’t provide that record. For example, if CloudKit fails to materialize an asset field, it returns an error instead of a partial record. CloudKit sorts the array according to the query’s sort descriptors.

`queryCursor`  
A cursor if the number of results exceeds `resultsLimit`; otherwise, `nil`.

If you specify `resultsLimit` and the number of matched records exceeds that value, CloudKit provides only that number of records and a *cursor* — an object that marks a specific location in the full search results. To retrieve the next subset of search results, pass that cursor to the fetch(withCursor:desiredKeys:resultsLimit:completionHandler:) method.

For information on a more configurable way to search a database, see CKQueryOperation.

## See Also

### Querying Records

func records(matching: CKQuery, inZoneWith: CKRecordZone.ID?, desiredKeys: [CKRecord.FieldKey]?, resultsLimit: Int) async throws -> (matchResults: [(CKRecord.ID, Result&lt;CKRecord, any Error>)], queryCursor: CKQueryOperation.Cursor?)

Searches for records that match a predicate and returns them to an awaiting caller.

func records(continuingMatchFrom: CKQueryOperation.Cursor, desiredKeys: [CKRecord.FieldKey]?, resultsLimit: Int) async throws -> (matchResults: [(CKRecord.ID, Result&lt;CKRecord, any Error>)], queryCursor: CKQueryOperation.Cursor?)

Retrieves the next batch of records from an existing search and returns them to an awaiting caller.

func fetch(withCursor: CKQueryOperation.Cursor, desiredKeys: [CKRecord.FieldKey]?, resultsLimit: Int, completionHandler: (Result&lt;(matchResults: [(CKRecord.ID, Result&lt;CKRecord, any Error>)], queryCursor: CKQueryOperation.Cursor?), any Error>) -> Void)

Retrieves the next batch of records from an existing search and delivers them to a completion handler.

func perform(CKQuery, inZoneWith: CKRecordZone.ID?, completionHandler: ([CKRecord]?, (any Error)?) -> Void)

Searches for records matching a predicate in the specified record zone.

Deprecated

func records(matching: CKQuery, inZoneWith: CKRecordZone.ID?) async throws -> [CKRecord]

Searches for records in the specified record zone and returns them to an awaiting caller.

Deprecated

