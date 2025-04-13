

- UIKit
- UICollectionViewDelegate
-  collectionView(\_:targetIndexPathForMoveOfItemFromOriginalIndexPath:atCurrentIndexPath:toProposedIndexPath:) 

Instance Method

# collectionView(\_:targetIndexPathForMoveOfItemFromOriginalIndexPath:atCurrentIndexPath:toProposedIndexPath:)

Asks the delegate for the index path to use when moving an item.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+tvOS 15.0+visionOS 1.0+

``` source
@MainActor
optional func collectionView(
    _ collectionView: UICollectionView,
    targetIndexPathForMoveOfItemFromOriginalIndexPath originalIndexPath: IndexPath,
    atCurrentIndexPath currentIndexPath: IndexPath,
    toProposedIndexPath proposedIndexPath: IndexPath
) -> IndexPath
```

## Parameters 

`collectionView`  

The collection view making the request.

`originalIndexPath`  

The item’s original index path. This value doesn’t change as the user interactively moves the item.

`currentIndexPath`  

The item’s current index path. This value changes as the user interactively moves the item, reflecting the item’s current position in the collection view.

`proposedIndexPath`  

The proposed index path of the item.

## Return Value

The index path you want to use for the item. If you don’t implement this method, the collection view uses the index path in the `proposedIndexPath` parameter.

## Discussion

During the interactive moving of an item, the collection view calls this method to see if you want to provide a different index path than the proposed path. You might use this method to prevent the user from dropping the item in an invalid location. For example, you might prevent the user from dropping the item in a specific section.

## See Also

### Handling layout changes

func collectionView(UICollectionView, transitionLayoutForOldLayout: UICollectionViewLayout, newLayout: UICollectionViewLayout) -> UICollectionViewTransitionLayout

Asks for the custom transition layout to use when moving between the specified layouts.

func collectionView(UICollectionView, targetContentOffsetForProposedContentOffset: CGPoint) -> CGPoint

Gives the delegate an opportunity to customize the content offset for layout changes and animated updates.

