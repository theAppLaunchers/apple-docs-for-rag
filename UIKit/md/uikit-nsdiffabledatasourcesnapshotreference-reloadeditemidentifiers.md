

- UIKit
- NSDiffableDataSourceSnapshotReference
-  reloadedItemIdentifiers 

Instance Property

# reloadedItemIdentifiers

Identifies the items reloaded by the changes to the snapshot.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+tvOS 15.0+visionOS 1.0+

``` source
var reloadedItemIdentifiers: [Any] { get }
```

## Discussion

After you make updates to the snapshot, this method returns an array of identifiers corresponding to the items that the view reloads when you apply the snapshot to your data source.

## See Also

### Reloading data

func reconfigureItems(withIdentifiers: [Any])

Updates the data for the items you specify in the snapshot, preserving the existing cells for the items.

var reconfiguredItemIdentifiers: [Any]

Identifies the items reconfigured by the changes to the snapshot.

func reloadItems(withIdentifiers: [Any])

Reloads the data within the specified items in the snapshot.

func reloadSections(withIdentifiers: [Any])

Reloads the data within the specified sections of the snapshot.

var reloadedSectionIdentifiers: [Any]

Identifies the sections reloaded by the changes to the snapshot.

