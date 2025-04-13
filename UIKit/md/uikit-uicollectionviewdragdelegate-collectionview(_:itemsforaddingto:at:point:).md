

- UIKit
- UICollectionViewDragDelegate
-  collectionView(\_:itemsForAddingTo:at:point:) 

Instance Method

# collectionView(\_:itemsForAddingTo:at:point:)

Adds the specified items to an existing drag session.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
@MainActor
optional func collectionView(
    _ collectionView: UICollectionView,
    itemsForAddingTo session: any UIDragSession,
    at indexPath: IndexPath,
    point: CGPoint
) -> [UIDragItem]
```

## Parameters 

`collectionView`  

The collection view from which the drag operation originated.

`session`  

The current drag session object.

`indexPath`  

The index path of the item to add to the drag.

`point`  

The point that the user touched. This point is in the coordinate space of the collection view.

## Return Value

An array of UIDragItem objects containing the items to add to the current drag session. Return an empty array to prevent the items from being added to the drag session.

## Discussion

Implement this method when you want to allow the user to add items to an active drag session. If you don’t implement this method, taps in the collection view trigger the selection of items or other behaviors. However, when a drag session is active and a tap occurs, the collection view calls this method to give you an opportunity to add the underlying item to the drag session.

In your implementation, create one or more UIDragItem objects for the item at the specified `indexPath`. Normally, you return only one drag item, but if the specified item has children or can’t be dragged without one or more associated items, include those items as well.

## See Also

### Providing the items to drag

func collectionView(UICollectionView, itemsForBeginning: any UIDragSession, at: IndexPath) -> [UIDragItem]

Provides the initial set of items (if any) to drag.

**Required**

