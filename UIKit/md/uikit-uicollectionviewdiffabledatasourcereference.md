

- UIKit
-  UICollectionViewDiffableDataSourceReference 

Class

# UICollectionViewDiffableDataSourceReference

The object you use to manage data and provide cells for a collection view.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+tvOS 13.0+visionOS 1.0+

``` source
@MainActor
class UICollectionViewDiffableDataSourceReference
```

## Overview

Important

If you’re working in a Swift codebase, always use UICollectionViewDiffableDataSource instead.

A *diffable data source* object is a specialized type of data source that works together with your collection view object. It provides the behavior you need to manage updates to your collection view’s data and UI in a simple, efficient way. It also conforms to the UICollectionViewDataSource protocol and provides implementations for all of the protocol’s methods.

To fill a collection view with data:

1.  Connect a diffable data source to your collection view.

2.  Implement a cell provider to configure your collection view’s cells.

3.  Generate the current state of the data.

4.  Display the data in the UI.

To connect a diffable data source to a collection view, you create the diffable data source using its init(collectionView:cellProvider:) initializer, passing in the collection view you want to associate with that data source. You also pass in a cell provider, where you configure each of your cells to determine how to display your data in the UI.

```
```

Then, you generate the current state of the data and display the data in the UI by constructing and applying a snapshot. For more information, see NSDiffableDataSourceSnapshotReference.

Important

Don’t change the dataSource on the collection view after you configure it with a diffable data source. If the collection view needs a new data source after you configure it initially, create and configure a new collection view and diffable data source.

## Topics

### Creating a diffable data source

init(collectionView: UICollectionView, cellProvider: UICollectionViewDiffableDataSourceReferenceCellProvider)

Creates a diffable data source with the specified cell provider, and connects it to the specified collection view.

typealias UICollectionViewDiffableDataSourceReferenceCellProvider

A closure that configures and returns a cell for a collection view from its diffable data source.

### Creating supplementary views

var supplementaryViewProvider: UICollectionViewDiffableDataSourceReferenceSupplementaryViewProvider?

The closure that configures and returns the collection view’s supplementary views, such as headers and footers, from the diffable data source.

typealias UICollectionViewDiffableDataSourceReferenceSupplementaryViewProvider

A closure that configures and returns a collection view’s supplementary view, such as a header or footer, from a diffable data source.

### Identifying items

func itemIdentifier(for: IndexPath) -> Any?

Returns an identifier for the item at the specified index path in the collection view.

func indexPath(forItemIdentifier: Any) -> IndexPath?

Returns an index path for the item with the specified identifier in the collection view.

### Identifying sections

func sectionIdentifier(for: Int) -> Any?

Returns an identifier for the section at the index you specify in the collection view.

func index(forSectionIdentifier: Any) -> Int

Returns an index for the section with the identifier you specify in the collection view.

### Updating data

func snapshot() -> NSDiffableDataSourceSnapshotReference

Returns a representation of the current state of the data in the collection view.

func applySnapshot(NSDiffableDataSourceSnapshotReference, animatingDifferences: Bool)

Updates the UI to reflect the state of the data in the snapshot, optionally animating the UI changes.

func applySnapshot(NSDiffableDataSourceSnapshotReference, animatingDifferences: Bool, completion: (() -> Void)?)

Updates the UI to reflect the state of the data in the snapshot, optionally animating the UI changes and executing a completion handler.

func applySnapshot(usingReloadData: NSDiffableDataSourceSnapshotReference)

Resets the UI to reflect the state of the data in the snapshot without computing a diff or animating the changes.

func applySnapshot(usingReloadData: NSDiffableDataSourceSnapshotReference, completion: (() -> Void)?)

Resets the UI to reflect the state of the data in the snapshot without computing a diff or animating the changes, optionally executing a completion handler.

### Updating section data

func snapshot(forSection: Any) -> NSDiffableDataSourceSectionSnapshotReference

Returns a representation of the current state of the data in the specified section of the collection view.

func applySnapshot(NSDiffableDataSourceSectionSnapshotReference, toSection: Any, animatingDifferences: Bool, completion: (() -> Void)?)

Updates the section UI to reflect the state of the data in the specified snapshot, optionally animating the UI changes and executing a completion handler.

func applySnapshot(NSDiffableDataSourceSectionSnapshotReference, toSection: Any, animatingDifferences: Bool)

Updates the section UI to reflect the state of the data in the specified snapshot, optionally animating the UI changes.

### Supporting reordering

var reorderingHandlers: __UICollectionViewDiffableDataSourceReorderingHandlers

The diffable data source’s handlers for reordering items.

### Supporting expanding and collapsing

var sectionSnapshotHandlers: __UICollectionViewDiffableDataSourceSectionSnapshotHandlers

The diffable data source’s handlers for expanding and collapsing items.

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
- UICollectionViewDataSource

