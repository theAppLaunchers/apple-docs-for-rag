

- UIKit
- UICollectionViewDelegateFlowLayout
-  collectionView(\_:layout:referenceSizeForFooterInSection:) 

Instance Method

# collectionView(\_:layout:referenceSizeForFooterInSection:)

Asks the delegate for the size of the footer view in the specified section.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
optional func collectionView(
    _ collectionView: UICollectionView,
    layout collectionViewLayout: UICollectionViewLayout,
    referenceSizeForFooterInSection section: Int
) -> CGSize
```

## Parameters 

`collectionView`  

The collection view object displaying the flow layout.

`collectionViewLayout`  

The layout object requesting the information.

`section`  

The index of the section whose footer size is being requested.

## Return Value

The size of the footer. If you return a value of size (0, 0), no footer is added.

## Discussion

If you do not implement this method, the flow layout uses the value in its footerReferenceSize property to set the size of the footer.

During layout, only the size that corresponds to the appropriate scrolling direction is used. For example, for the vertical scrolling direction, the layout object uses the height value specified by this property. (In that instance, the width of the footer would be set to the width of the collection view.) If the size in the appropriate scrolling dimension is 0, no footer is added.

## See Also

### Getting the header and footer sizes

func collectionView(UICollectionView, layout: UICollectionViewLayout, referenceSizeForHeaderInSection: Int) -> CGSize

Asks the delegate for the size of the header view in the specified section.

