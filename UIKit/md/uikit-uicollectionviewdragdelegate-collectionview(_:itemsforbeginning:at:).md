

- UIKit
- UICollectionViewDragDelegate
-  collectionView(\_:itemsForBeginning:at:) 

Instance Method

# collectionView(\_:itemsForBeginning:at:)

Provides the initial set of items (if any) to drag.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
@MainActor
func collectionView(
    _ collectionView: UICollectionView,
    itemsForBeginning session: any UIDragSession,
    at indexPath: IndexPath
) -> [UIDragItem]
```

**Required**

## Parameters 

`collectionView`  

The collection view from which the drag operation originated.

`session`  

The current drag session object.

`indexPath`  

The index path of the item to drag.

## Return Value

An array of UIDragItem objects containing the details of the items to drag. Return an empty array to prevent the item from being dragged.

## Mentioned in 

Supporting Drag and Drop in Collection Views

## Discussion

You must implement this method to allow the dragging of items from your collection view. In your implementation, create one or more UIDragItem objects for the item at the specified `indexPath`. Normally, you return only one drag item, but if the specified item has children or can’t be dragged without one or more associated items, include those items as well.

The collection view calls this method one or more times when a new drag begins within its bounds. Specifically, if the user begins the drag from a selected item, the collection view calls this method once for each item that’s part of the selection. If the user begins the drag from an unselected item, the collection view calls the method only once for that item.

## See Also

### Providing the items to drag

func collectionView(UICollectionView, itemsForAddingTo: any UIDragSession, at: IndexPath, point: CGPoint) -> [UIDragItem]

Adds the specified items to an existing drag session.

