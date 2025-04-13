

- Foundation
- Numbers, Data, and Basic Values
- NSURL
- URLResourceKey
-  Checking Volume Storage Capacity 

Article

# Checking Volume Storage Capacity

Confirm that you have enough local storage space for a large amount of data.

## Overview

Before you try to store a large amount of data locally, first verify that you have sufficient storage capacity. To get the storage capacity of a volume, you construct a URL (using an instance of URL) that references an object on the volume to be queried, and then query that volume.

### Decide Which Query Type to Use

The query type to use depends on what’s being stored. If you’re storing data based on a user request or resources the app requires to function properly (for example, a video the user is about to watch or resources that are needed for the next level in a game), query against volumeAvailableCapacityForImportantUsageKey. However, if you’re downloading data in a more predictive manner (for example, downloading a newly available episode of a TV series that the user has been watching recently), query against volumeAvailableCapacityForOpportunisticUsageKey.

### Construct a Query

Use this example as a guide to construct your own query:

- Swift
- Objective-C

```
let fileURL = URL(fileURLWithPath:"/")
do {
    let values = try fileURL.resourceValues(forKeys: [.volumeAvailableCapacityForImportantUsageKey])
    if let capacity = values.volumeAvailableCapacityForImportantUsage {
        print("Available capacity for important usage: \(capacity)")
    } else {
        print("Capacity is unavailable")
    }
} catch {
    print("Error retrieving capacity: \(error.localizedDescription)")
}
```

```
NSURL *fileURL = [[NSURL alloc] initFileURLWithPath:@"/"];
NSError *error = nil;
NSDictionary *results = [fileURL resourceValuesForKeys:@[NSURLVolumeAvailableCapacityForImportantUsageKey] error:&error];
if (!results) {
    NSLog(@"Error retrieving resource keys: %@\n%@", [error localizedDescription], [error userInfo]);
    abort();
}
NSLog(@"Available capacity for important usage: %@", results[NSURLVolumeAvailableCapacityForImportantUsageKey]);
```

## See Also

### Volume capacity keys

static let volumeAvailableCapacityKey: URLResourceKey

Key for the volume’s available capacity in bytes (read-only).

static let volumeAvailableCapacityForImportantUsageKey: URLResourceKey

Key for the volume’s available capacity in bytes for storing important resources (read-only).

static let volumeAvailableCapacityForOpportunisticUsageKey: URLResourceKey

Key for the volume’s available capacity in bytes for storing nonessential resources (read-only).

static let volumeTotalCapacityKey: URLResourceKey

Key for the volume’s total capacity in bytes (read-only).

