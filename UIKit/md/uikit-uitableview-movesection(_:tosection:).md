

- UIKit
- UITableView
-  moveSection(\_:toSection:) 

Instance Method

# moveSection(\_:toSection:)

Moves a section to a new location in the table view.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
func moveSection(
    _ section: Int,
    toSection newSection: Int
)
```

## Parameters 

`section`  

The index of the section to move.

`newSection`  

The index in the table view that’s the destination of the move for the section. The existing section at that location slides up or down to an adjoining index position to make room for it.

## Discussion

You can combine section-move operations with section-insertion and section-deletion operations within a beginUpdates()–endUpdates() block to have all changes occur together as a single animation.

Unlike the section-insertion section row-deletion methods, this method doesn’t take an animation parameter. For sections that are moved, the moved section animates straight from the starting position to the ending position. Also unlike the other methods, this method allows only one section to be moved per call. If you want multiple section moved, call this method repeatedly within a beginUpdates()–endUpdates() block.

## See Also

### Inserting, deleting, and moving rows and sections

func insertRows(at: [IndexPath], with: UITableView.RowAnimation)

Inserts rows in the table view at the locations that an array of index paths identifies, with an option to animate the insertion.

func deleteRows(at: [IndexPath], with: UITableView.RowAnimation)

Deletes the rows that an array of index paths identifies, with an option to animate the deletion.

func insertSections(IndexSet, with: UITableView.RowAnimation)

Inserts one or more sections in the table view, with an option to animate the insertion.

func deleteSections(IndexSet, with: UITableView.RowAnimation)

Deletes one or more sections in the table view, with an option to animate the deletion.

enum RowAnimation

The type of animation to use when inserting or deleting rows.

func moveRow(at: IndexPath, to: IndexPath)

Moves the row at a specified location to a destination location.

