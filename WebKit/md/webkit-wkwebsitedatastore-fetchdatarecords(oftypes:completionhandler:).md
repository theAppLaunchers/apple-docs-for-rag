

- WebKit
- WKWebsiteDataStore
-  fetchDataRecords(ofTypes:completionHandler:) 

Instance Method

# fetchDataRecords(ofTypes:completionHandler:)

Fetches the specified types of records from the data store.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+visionOS 1.0+

``` source
@MainActor
func fetchDataRecords(
    ofTypes dataTypes: Set,
    completionHandler: @escaping @MainActor ([WKWebsiteDataRecord]) -> Void
)
```

``` source
@MainActor
func dataRecords(ofTypes dataTypes: Set) async -> [WKWebsiteDataRecord]
```

## Parameters 

`dataTypes`  

The types of records to fetch. For a list of all possible types, see Data Store Record Types. To specify all types, specify the set returned by the allWebsiteDataTypes() method.

`completionHandler`  

The completion handler block to execute asynchronously with the results. This block has no return value and takes the following parameter:

dataRecordArray  
An array of WKWebsiteDataRecord objects. Each object in this array corresponds to data for one of the requested types. If no records of the requested types exist, this array is empty.

## Discussion

Call this method to retrieve information about the types of data that the website saves. The returned records don’t include the data itself, but contain information that you can convey to the user. For example, you might use the returned data records to display the cookies a website uses, or to show which websites cache data.

## See Also

### Retrieving specific types of data

class func allWebsiteDataTypes() -> Set&lt;String>

Returns the set of all the available data types.

