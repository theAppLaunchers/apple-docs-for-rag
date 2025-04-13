

- AppKit
- NSCollectionView
-  reloadSections(\_:) 

Instance Method

# reloadSections(\_:)

Reloads the data in the specified sections of the collection view.

macOS 10.11+

``` source
@MainActor
func reloadSections(_ sections: IndexSet)
```

## Parameters 

`sections`  

The indexes of the sections that you want to reload. Specifying `nil` for this parameter raises an exception.

## Discussion

Call this method when the data for the specified sections changes or when you want to force the appearance of those sections to be updated. When you call this method, the collection view discards visible elements in the section along with any cached attributes for those elements. For efficiency, it then asks the layout object to provide fresh attributes for only the visible items and views and requests new views for those elements.

Do not call this method in the middle of animation blocks where items are being inserted or deleted. The methods used to insert and delete items automatically update the collection view’s contents.

## See Also

### Reloading Content

func reloadData()

Reloads all of the data for the collection view.

func reloadItems(at: Set&lt;IndexPath>)

Reloads only the specified items.

