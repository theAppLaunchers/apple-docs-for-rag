

- CloudKit
- CKRecordZone
- CKRecordZone.Capabilities
-  fetchChanges 

Type Property

# fetchChanges

A capability for fetching only the changed records from a zone.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOSvisionOS 1.0+watchOS 3.0+

``` source
static var fetchChanges: CKRecordZone.Capabilities { get }
```

## Discussion

This capability makes the creation of offline caches more efficient. Instead of fetching the entire record every time, use CKFetchRecordZoneChangesOperation to fetch only the changed values, and use the data it returns to update your cache. This minimizes the amount of data you receive from the server.

## See Also

### Zone Capabilities

static var atomic: CKRecordZone.Capabilities

A capability that allows atomic changes of multiple records.

static var sharing: CKRecordZone.Capabilities

A capability for sharing a specific hierarchy of records.

static var zoneWideSharing: CKRecordZone.Capabilities

A capability for sharing the entire contents of a record zone.

