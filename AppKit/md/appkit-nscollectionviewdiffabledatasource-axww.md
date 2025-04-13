

- AppKit
-  NSCollectionViewDiffableDataSource 

Class

# NSCollectionViewDiffableDataSource

The object you use to manage data and provide items for a collection view.

macOS 10.15.1+

``` source
class NSCollectionViewDiffableDataSource where SectionIdentifierType : Hashable, ItemIdentifierType : Hashable
```

## Overview

A *diffable data source* object is a specialized type of data source that works together with your collection view object. It provides the behavior you need to manage updates to your collection view’s data and UI in a simple, efficient way. It also conforms to the NSCollectionViewDataSource protocol and provides implementations for all of the protocol’s methods.

To fill a collection view with data:

1.  Connect a diffable data source to your collection view.

2.  Implement an item provider to configure your collection view’s items.

3.  Generate the current state of the data.

4.  Display the data in the UI.

To connect a diffable data source to a collection view, you create the diffable data source using its init(collectionView:itemProvider:) initializer, passing in the collection view you want to associate with that data source. You also pass in an item provider, where you configure each of your items to determine how to display your data in the UI.

```
dataSource = NSCollectionViewDiffableDataSource(collectionView: collectionView) {
    (collectionView: NSCollectionView, indexPath: IndexPath, itemIdentifier: UUID) -> NSCollectionViewItem? in
    // configure and return item
}
```

Then, you generate the current state of the data and display the data in the UI by constructing and applying a snapshot. For more information, see NSDiffableDataSourceSnapshot.

## Topics

### Creating a Diffable Data Source

init(collectionView: NSCollectionView, itemProvider: NSCollectionViewDiffableDataSource&lt;SectionIdentifierType, ItemIdentifierType>.ItemProvider)

Creates a diffable data source with the specified item provider, and connects it to the specified collection view.

typealias ItemProvider

A closure that configures and returns an item for a collection view from its diffable data source.

### Creating Supplementary Views

var supplementaryViewProvider: NSCollectionViewDiffableDataSource&lt;SectionIdentifierType, ItemIdentifierType>.SupplementaryViewProvider?

The closure that configures and returns the collection view’s supplementary views, such as headers and footers, from the diffable data source.

typealias SupplementaryViewProvider

A closure that configures and returns a collection view’s supplementary view, such as a header or footer, from a diffable data source.

### Identifying Items

func itemIdentifier(for: IndexPath) -> ItemIdentifierType?

Returns an identifier for the item at the specified index path in the collection view.

func indexPath(for: ItemIdentifierType) -> IndexPath?

Returns an index path for the item with the specified identifier in the collection view.

### Updating Data

func snapshot() -> NSDiffableDataSourceSnapshot&lt;SectionIdentifierType, ItemIdentifierType>

Returns a representation of the current state of the data in the collection view.

func apply(NSDiffableDataSourceSnapshot&lt;SectionIdentifierType, ItemIdentifierType>, animatingDifferences: Bool, completion: (() -> Void)?)

Updates the UI to reflect the state of the data in the specified snapshot, optionally animating the UI changes and executing a completion handler.

### Supporting Protocol Requirements

Protocol Implementations

Access the diffable data source’s implementations of protocol methods.

### Instance Methods

func description() -> String

Returns a string with a description of the diffable data source.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCollectionViewDataSource
- NSObjectProtocol

## See Also

### Data

protocol NSCollectionViewDataSource

A set of methods that a data source object implements to provide the information and view objects that a collection view requires to present content.

protocol NSCollectionViewDelegate

A set of methods that you use to manage the behavior of a collection view.

struct NSDiffableDataSourceSnapshot

A representation of the state of the data in a view at a specific point in time.

