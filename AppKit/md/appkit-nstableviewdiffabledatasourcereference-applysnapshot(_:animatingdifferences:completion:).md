

- AppKit
- NSTableViewDiffableDataSourceReference
-  applySnapshot(\_:animatingDifferences:completion:) 

Instance Method

# applySnapshot(\_:animatingDifferences:completion:)

Updates the UI to reflect the state of the data in the specified snapshot, optionally animating the UI changes and executing a completion handler.

macOS 11.0+

``` source
func applySnapshot(
    _ snapshot: NSDiffableDataSourceSnapshotReference,
    animatingDifferences: Bool,
    completion: (() -> Void)? = nil
)
```

``` source
func applySnapshot(
    _ snapshot: NSDiffableDataSourceSnapshotReference,
    animatingDifferences: Bool
) async
```

## Parameters 

`snapshot`  

The snapshot that reflects the new state of the data in the table view.

`animatingDifferences`  

If `true`, the diffable data source computes the difference between the table view’s current state and the new state in the snapshot, which is an O(n) operation, where n is the number of items in the snapshot. The system animates the differences in the UI between the current state and new state. If `false`, the system sets the table view UI to the new state without any animations, with no additional overhead for computing a diff. Any ongoing row animations are interrupted and the table view’s content immediately reloads.

`completion`  

The closure the system executes when the animations are complete. This closure has no return value and takes no parameters. The system calls this closure from the main queue.

## Discussion

## See Also

### Updating Data

func snapshot() -> NSDiffableDataSourceSnapshotReference

Returns a representation of the current state of the data in the table view.

func applySnapshot(NSDiffableDataSourceSnapshotReference, animatingDifferences: Bool)

Updates the UI to reflect the state of the data in the specified snapshot, optionally animating the UI changes.

var defaultRowAnimation: NSTableView.AnimationOptions

The default animation the UI uses to show differences between rows.

