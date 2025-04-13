

- AppKit
- NSCollectionViewLayout
-  layoutAttributesForSupplementaryView(ofKind:at:) 

Instance Method

# layoutAttributesForSupplementaryView(ofKind:at:)

Returns the layout attributes of the supplementary view at the specified location in your layout.

macOS

``` source
@MainActor
func layoutAttributesForSupplementaryView(
    ofKind elementKind: NSCollectionView.SupplementaryElementKind,
    at indexPath: IndexPath
) -> NSCollectionViewLayoutAttributes?
```

## Parameters 

`elementKind`  

A string that identifies the type of the supplementary view. Use this string to differentiate the supplementary views in a given section.

`indexPath`  

The index path of the supplementary view. Use this parameter to determine which section contains the supplementary view.

## Return Value

A layout attributes object containing the layout information to apply to the supplementary view.

## Discussion

If your layout includes supplementary views, you must override this method. In your implementation, create an instance of the appropriate layout attributes class and fill the resulting object with the layout information for the corresponding supplementary view. You define the supported supplementary views by assigning each one a string that identifies its kind. Use the `elementKind` and `indexPath` properties to identify the specific supplementary view whose attributes were requested.

You can call this method from other layout-related methods when you want to retrieve layout information for supplementary views. Call this method only for supplementary views. Do not call it to retrieve layout attributes for items or decoration views.

## See Also

### Providing Layout Information

class var layoutAttributesClass: AnyClass

Returns the class to use for layout attribute objects

func prepare()

Prepares the layout object to begin laying out content.

var collectionViewContentSize: NSSize

The width and height of the collection view’s contents.

func layoutAttributesForElements(in: NSRect) -> [NSCollectionViewLayoutAttributes]

Returns the layout attribute objects for all items and views in the specified rectangle.

func layoutAttributesForItem(at: IndexPath) -> NSCollectionViewLayoutAttributes?

Returns the layout attributes for the item at the specified index path.

func layoutAttributesForDecorationView(ofKind: NSCollectionView.DecorationElementKind, at: IndexPath) -> NSCollectionViewLayoutAttributes?

Returns the layout attributes of the decoration view at the specified location in your layout.

func layoutAttributesForDropTarget(at: NSPoint) -> NSCollectionViewLayoutAttributes?

Returns layout attributes for the drop target at the specified point.

func layoutAttributesForInterItemGap(before: IndexPath) -> NSCollectionViewLayoutAttributes?

Returns layout attributes for the inter-item gap at the specified location in your layout.

func targetContentOffset(forProposedContentOffset: NSPoint) -> NSPoint

Returns the offset value to use after an animated layout update or change.

func targetContentOffset(forProposedContentOffset: NSPoint, withScrollingVelocity: NSPoint) -> NSPoint

Returns the offset value to use for the collection view’s content at the end of scrolling.

