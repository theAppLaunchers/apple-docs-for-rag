

- UIKit
- UICollectionView
-  deleteSections(\_:) 

Instance Method

# deleteSections(\_:)

Deletes the sections at the specified indexes.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
func deleteSections(_ sections: IndexSet)
```

## Parameters 

`sections`  

The indexes of the sections you want to delete. This parameter must not be `nil`.

## Discussion

Use this method to remove the sections and their items from the collection view. You might do this when you remove the sections from your data source object or in response to user interactions with the collection view. The collection view updates the layout of the remaining sections and items to account for the deletions, animating the remaining items into position as needed.

You can also call this method from a block passed to the performBatchUpdates(_:completion:) method when you want to animate multiple separate changes into place at the same time. See the description of that method for more information.

## See Also

### Inserting, moving, and deleting sections

func insertSections(IndexSet)

Inserts new sections at the specified indexes.

func moveSection(Int, toSection: Int)

Moves a section from one location to another in the collection view.

