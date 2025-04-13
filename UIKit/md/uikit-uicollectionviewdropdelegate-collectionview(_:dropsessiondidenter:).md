

- UIKit
- UICollectionViewDropDelegate
-  collectionView(\_:dropSessionDidEnter:) 

Instance Method

# collectionView(\_:dropSessionDidEnter:)

Notifies you when dragged content enters the collection view’s bounds rectangle.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
@MainActor
optional func collectionView(
    _ collectionView: UICollectionView,
    dropSessionDidEnter session: any UIDropSession
)
```

## Parameters 

`collectionView`  

The collection view that’s tracking the dragged content.

`session`  

The drop session object containing information about the type of data being dragged.

## Discussion

The collection view calls this method when dragged content enters its bounds rectangle. The method isn’t called again until the dragged content exits the collection view’s bounds (triggering a call to the collectionView(_:dropSessionDidExit:) method) and enters again.

Use this method to perform any one-time setup associated with tracking dragged content over the collection view.

## See Also

### Tracking the drag movements

func collectionView(UICollectionView, dropSessionDidUpdate: any UIDropSession, withDestinationIndexPath: IndexPath?) -> UICollectionViewDropProposal

Tells your delegate that the position of the dragged data over the collection view changed.

func collectionView(UICollectionView, dropSessionDidExit: any UIDropSession)

Notifies you when dragged content exits the collection view’s bounds rectangle.

func collectionView(UICollectionView, dropSessionDidEnd: any UIDropSession)

Notifies you when the drag operation ends.

