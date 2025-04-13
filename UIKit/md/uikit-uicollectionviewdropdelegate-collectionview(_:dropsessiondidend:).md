

- UIKit
- UICollectionViewDropDelegate
-  collectionView(\_:dropSessionDidEnd:) 

Instance Method

# collectionView(\_:dropSessionDidEnd:)

Notifies you when the drag operation ends.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
@MainActor
optional func collectionView(
    _ collectionView: UICollectionView,
    dropSessionDidEnd session: any UIDropSession
)
```

## Parameters 

`collectionView`  

The collection view that’s tracking the dragged content.

`session`  

The drop session object containing information about the data being dragged.

## Discussion

The collection view calls this method at the conclusion of a drag that was over the collection view at one point. Use it to clean up any state information that you used to handle the drag. This method is called regardless of whether the data was actually dropped onto the collection view.

## See Also

### Tracking the drag movements

func collectionView(UICollectionView, dropSessionDidUpdate: any UIDropSession, withDestinationIndexPath: IndexPath?) -> UICollectionViewDropProposal

Tells your delegate that the position of the dragged data over the collection view changed.

func collectionView(UICollectionView, dropSessionDidEnter: any UIDropSession)

Notifies you when dragged content enters the collection view’s bounds rectangle.

func collectionView(UICollectionView, dropSessionDidExit: any UIDropSession)

Notifies you when dragged content exits the collection view’s bounds rectangle.

