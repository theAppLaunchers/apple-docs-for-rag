

- UIKit
- UICollectionViewLayout
-  indexPathsToDeleteForDecorationView(ofKind:) 

Instance Method

# indexPathsToDeleteForDecorationView(ofKind:)

Retrieves an array of index paths representing the decoration views to remove.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
func indexPathsToDeleteForDecorationView(ofKind elementKind: String) -> [IndexPath]
```

## Parameters 

`elementKind`  

The specific type of decoration view.

## Return Value

An array of NSIndexPath objects indicating the decoration views you want to remove or an empty array if you do not want to remove any views of the given kind.

## Discussion

The collection view calls this method whenever you delete cells or sections to the collection view. Implementing this method gives your layout object an opportunity to remove any decoration views that are no longer needed.

The collection view calls this method between its calls to prepare(forCollectionViewUpdates:) and finalizeCollectionViewUpdates().

## See Also

### Responding to collection view updates

func prepare(forCollectionViewUpdates: [UICollectionViewUpdateItem])

Notifies the layout object that the contents of the collection view are about to change.

func finalizeCollectionViewUpdates()

Performs any additional animations or clean up needed during a collection view update.

func indexPathsToInsertForSupplementaryView(ofKind: String) -> [IndexPath]

Retrieves an array of index paths for the supplementary views you want to add to the layout.

func indexPathsToInsertForDecorationView(ofKind: String) -> [IndexPath]

Retrieves an array of index paths representing the decoration views to add.

func initialLayoutAttributesForAppearingItem(at: IndexPath) -> UICollectionViewLayoutAttributes?

Retrieves the starting layout information for an item being inserted into the collection view.

func initialLayoutAttributesForAppearingSupplementaryElement(ofKind: String, at: IndexPath) -> UICollectionViewLayoutAttributes?

Retrieves the starting layout information for a supplementary view being inserted into the collection view.

func initialLayoutAttributesForAppearingDecorationElement(ofKind: String, at: IndexPath) -> UICollectionViewLayoutAttributes?

Retrieves the starting layout information for a decoration view being inserted into the collection view.

func indexPathsToDeleteForSupplementaryView(ofKind: String) -> [IndexPath]

Retrieves an array of index paths representing the supplementary views to remove.

func finalLayoutAttributesForDisappearingItem(at: IndexPath) -> UICollectionViewLayoutAttributes?

Retrieves the final layout information for an item that is about to be removed from the collection view.

func finalLayoutAttributesForDisappearingSupplementaryElement(ofKind: String, at: IndexPath) -> UICollectionViewLayoutAttributes?

Retrieves the final layout information for a supplementary view that is about to be removed from the collection view.

func finalLayoutAttributesForDisappearingDecorationElement(ofKind: String, at: IndexPath) -> UICollectionViewLayoutAttributes?

Retrieves the final layout information for a decoration view that is about to be removed from the collection view.

func targetIndexPath(forInteractivelyMovingItem: IndexPath, withPosition: CGPoint) -> IndexPath

Retrieves the index path to for an item when it is at the specified location in the collection view’s bounds.

