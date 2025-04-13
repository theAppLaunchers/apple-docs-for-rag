

- UIKit
-  UITableViewDiffableDataSourceReference 

Class

# UITableViewDiffableDataSourceReference

The object you use to manage data and provide cells for a table view.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+tvOS 13.0+visionOS 1.0+

``` source
@MainActor
class UITableViewDiffableDataSourceReference
```

## Overview

Important

If you’re working in a Swift codebase, always use UITableViewDiffableDataSource instead.

A *diffable data source* object is a specialized type of data source that works together with your table view object. It provides the behavior you need to manage updates to your table view’s data and UI in a simple, efficient way. It also conforms to the UITableViewDataSource protocol and provides implementations for all of the protocol’s methods.

To fill a table view with data:

1.  Connect a diffable data source to your table view.

2.  Implement a cell provider to configure your table view’s cells.

3.  Generate the current state of the data.

4.  Display the data in the UI.

To connect a diffable data source to a table view, you create the diffable data source using its init(tableView:cellProvider:) initializer, passing in the table view you want to associate with that data source. You also pass in a cell provider, where you configure each of your cells to determine how to display your data in the UI.

```
self.dataSource = [[UITableViewDiffableDataSource alloc] initWithTableView:self.tableView cellProvider:^UITableViewCell *(UITableView *tableView, NSIndexPath *indexPath, id itemIdentifier) {
    // configure and return cell
}];
```

Then, you generate the current state of the data and display the data in the UI by constructing and applying a snapshot. For more information, see NSDiffableDataSourceSnapshotReference.

Important

Do not change the dataSource on the table view after you configure it with a diffable data source. If the table view needs a new data source after you configure it initially, create and configure a new table view and diffable data source.

## Topics

### Creating a diffable data source

init(tableView: UITableView, cellProvider: UITableViewDiffableDataSourceReferenceCellProvider)

Creates a diffable data source with the specified cell provider, and connects it to the specified table view.

typealias UITableViewDiffableDataSourceReferenceCellProvider

A closure that configures and returns a cell for a table view from its diffable data source.

### Identifying items

func itemIdentifier(for: IndexPath) -> Any?

Returns an identifier for the item at the specified index path in the table view.

func indexPath(forItemIdentifier: Any) -> IndexPath?

Returns an index path for the item with the specified identifier in the table view.

### Identifying sections

func sectionIdentifier(for: Int) -> Any?

Returns an identifier for the section at the index you specify in the table view.

func index(forSectionIdentifier: Any) -> Int

Returns an index for the section with the identifier you specify in the table view.

### Updating data

func snapshot() -> NSDiffableDataSourceSnapshotReference

Returns a representation of the current state of the data in the table view.

func applySnapshot(NSDiffableDataSourceSnapshotReference, animatingDifferences: Bool)

Updates the UI to reflect the state of the data in the snapshot, optionally animating the UI changes.

func applySnapshot(NSDiffableDataSourceSnapshotReference, animatingDifferences: Bool, completion: (() -> Void)?)

Updates the UI to reflect the state of the data in the snapshot, optionally animating the UI changes and executing a completion handler.

func applySnapshot(usingReloadData: NSDiffableDataSourceSnapshotReference)

Resets the UI to reflect the state of the data in the snapshot without computing a diff or animating the changes.

func applySnapshot(usingReloadData: NSDiffableDataSourceSnapshotReference, completion: (() -> Void)?)

Resets the UI to reflect the state of the data in the snapshot without computing a diff or animating the changes, optionally executing a completion handler.

var defaultRowAnimation: UITableView.RowAnimation

The default type of animation to use when inserting or deleting rows.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol
- Sendable
- UITableViewDataSource

