

- AppKit
-  NSDiffableDataSourceSnapshotReference 

Class

# NSDiffableDataSourceSnapshotReference

A representation of the state of the data in a view at a specific point in time.

macOS 10.15+

``` source
class NSDiffableDataSourceSnapshotReference
```

## Overview

Important

If you’re working in a Swift codebase, always use NSDiffableDataSourceSnapshot instead of `NSDiffableDataSourceSnapshotReference`.

Diffable data sources use *snapshots* to provide data for collection views and table views. Through a snapshot, you set up the initial state of the data that displays in a view, and later update that data.

The data in a snapshot is made up of the sections and items you want to display, in the specific order you want to display them. You configure what to display by adding, deleting, or moving the sections and items.

Important

Each of your sections and items must have unique identifiers.

To display data in a view using a snapshot:

1.  Create a snapshot and populate it with the state of the data you want to display.

2.  Apply the snapshot to reflect the changes in the UI.

You can create and configure a snapshot in one of these ways:

- Create an empty snapshot, then append sections and items to it.

- Get the current snapshot by calling the diffable data source’s snapshot() method, then modify that snapshot to reflect the new state of the data that you want to display.

For example, the following code creates an empty snapshot, and populates it with a single section with three items. Then, it applies the snapshot, animating the UI updates between the previous state and the new state represented in the snapshot.

- Swift
- Objective-C

```
// Create a snapshot.
var snapshot = NSDiffableDataSourceSnapshot()        

// Populate the snapshot.
snapshot.appendSections([0])
snapshot.appendItems([UUID(), UUID(), UUID()])

// Apply the snapshot.
dataSource.apply(snapshot, animatingDifferences: true)
```

```
// Create a snapshot.
NSDiffableDataSourceSnapshot *snapshot = [[NSDiffableDataSourceSnapshot alloc] init];

// Populate the snapshot.
[snapshot appendSectionsWithIdentifiers:@[@0]];
[snapshot appendItemsWithIdentifiers:@[[NSUUID UUID], [NSUUID UUID], [NSUUID UUID]]];

// Apply the snapshot.
[self.dataSource applySnapshot:snapshot animatingDifferences:YES];
```

For more information, see the diffable data source types:

- UICollectionViewDiffableDataSource

- UITableViewDiffableDataSource

- NSCollectionViewDiffableDataSourceReference

### Bridging

Avoid using this type in Swift code. Only use this type to bridge from Objective-C code to Swift code by typecasting from a snapshot reference to a snapshot:

```
let snapshot = snapshotReference as NSDiffableDataSourceSnapshot
```

## Topics

### Creating a snapshot

func appendSections(withIdentifiers: [Any])

Adds the sections with the specified identifiers to the snapshot.

func appendItems(withIdentifiers: [Any], intoSectionWithIdentifier: Any)

Adds the items with the specified identifiers to the specified section of the snapshot.

func appendItems(withIdentifiers: [Any])

Adds the items with the specified identifiers to the last section of the snapshot.

### Getting item and section metrics

var numberOfItems: Int

The number of items in the snapshot.

var numberOfSections: Int

The number of sections in the snapshot.

func numberOfItems(inSection: Any) -> Int

Returns the number of items in the specified section of the snapshot.

### Identifying items and sections

var itemIdentifiers: [Any]

The identifiers of all of the items in the snapshot.

var sectionIdentifiers: [Any]

The identifiers of all of the sections in the snapshot.

func index(ofItemIdentifier: Any) -> Int

Returns the index of the item in the snapshot with the specified identifier.

func index(ofSectionIdentifier: Any) -> Int

Returns the index of the section of the snapshot with the specified identifier.

func itemIdentifiersInSection(withIdentifier: Any) -> [Any]

Returns the identifiers of all of the items in the specified section of the snapshot.

func sectionIdentifier(forSectionContainingItemIdentifier: Any) -> Any?

Returns the identifier of the section containing the specified item in the snapshot.

### Inserting items and sections

func insertItems(withIdentifiers: [Any], afterItemWithIdentifier: Any)

Inserts the provided items immediately after the item with the specified identifier in the snapshot.

func insertItems(withIdentifiers: [Any], beforeItemWithIdentifier: Any)

Inserts the provided items immediately before the item with the specified identifier in the snapshot.

func insertSections(withIdentifiers: [Any], afterSectionWithIdentifier: Any)

Inserts the provided sections immediately after the section with the specified identifier in the snapshot.

func insertSections(withIdentifiers: [Any], beforeSectionWithIdentifier: Any)

Inserts the provided sections immediately before the section with the specified identifier in the snapshot.

### Removing items and sections

func deleteAllItems()

Deletes all of the items from the snapshot.

func deleteItems(withIdentifiers: [Any])

Deletes the items with the specified identifiers from the snapshot.

func deleteSections(withIdentifiers: [Any])

Deletes the sections with the specified identifiers from the snapshot.

### Reordering items and sections

func moveItem(withIdentifier: Any, afterItemWithIdentifier: Any)

Moves the item from its current position in the snapshot to the position immediately after the specified item.

func moveItem(withIdentifier: Any, beforeItemWithIdentifier: Any)

Moves the item from its current position in the snapshot to the position immediately before the specified item.

func moveSection(withIdentifier: Any, afterSectionWithIdentifier: Any)

Moves the section from its current position in the snapshot to the position immediately after the specified section.

func moveSection(withIdentifier: Any, beforeSectionWithIdentifier: Any)

Moves the section from its current position in the snapshot to the position immediately before the specified section.

### Reloading data

func reloadItems(withIdentifiers: [Any])

Reloads the data within the specified items in the snapshot.

func reloadSections(withIdentifiers: [Any])

Reloads the data within the specified sections of the snapshot.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCopying
- NSObjectProtocol

