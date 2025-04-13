

- UIKit
- UICollectionView
-  performBatchUpdates(\_:completion:) 

Instance Method

# performBatchUpdates(\_:completion:)

Animates multiple insert, delete, reload, and move operations as a group.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
func performBatchUpdates(
    _ updates: (() -> Void)?,
    completion: ((Bool) -> Void)? = nil
)
```

## Parameters 

`updates`  

The block that performs the relevant insert, delete, reload, or move operations.

`completion`  

A completion handler block to execute when all of the operations finish. This block takes a single Boolean parameter that contains the value true if all of the related animations completed successfully or false if they were interrupted. This parameter may be `nil`.

## Discussion

You can use this method in cases where you want to make multiple changes to the collection view in one single animated operation, as opposed to in several separate animations. You might use this method to insert, delete, reload, or move cells or use it to change the layout parameters associated with one or more cells. Use the block passed in the `updates` parameter to specify all of the operations you want to perform.

If the collection view’s layout isn’t up to date before you call this method, a reload may occur. To avoid problems, you should update your data model inside the `updates` block or ensure the layout is updated before you call performBatchUpdates(_:completion:).

Deletes are processed before inserts in batch operations. This means the indexes for the deletions are processed relative to the indexes of the collection view’s state before the batch operation, and the indexes for the insertions are processed relative to the indexes of the state after all the deletions in the batch operation.

## See Also

### Related Documentation

func deleteItems(at: [IndexPath])

Deletes the items at the specified index paths.

func moveSection(Int, toSection: Int)

Moves a section from one location to another in the collection view.

func moveItem(at: IndexPath, to: IndexPath)

Moves an item from one location to another in the collection view.

func insertItems(at: [IndexPath])

Inserts new items at the specified index paths.

func insertSections(IndexSet)

Inserts new sections at the specified indexes.

func deleteSections(IndexSet)

Deletes the sections at the specified indexes.

