

- AppKit
- NSCollectionView
-  reloadItems(at:) 

Instance Method

# reloadItems(at:)

Reloads only the specified items.

macOS 10.11+

``` source
@MainActor
func reloadItems(at indexPaths: Set)
```

## Parameters 

`indexPaths`  

The index paths of the specific items that you want to reload. Specifying `nil` for this parameter raises an exception.

## Discussion

Call this method to update specific items in your collection view. You call this method when the underlying data for those items changes and you want to update the visual appearance of those items. When you call this method, the collection view discards the specified items and asks your data source to provide new ones. For efficiency, the collection view requests only the items that are visible.

## See Also

### Reloading Content

func reloadData()

Reloads all of the data for the collection view.

func reloadSections(IndexSet)

Reloads the data in the specified sections of the collection view.

