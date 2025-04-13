

- AppKit
- NSCollectionView
-  numberOfItems(inSection:) 

Instance Method

# numberOfItems(inSection:)

Returns the number of items in the specified section.

macOS 10.11+

``` source
@MainActor
func numberOfItems(inSection section: Int) -> Int
```

## Parameters 

`section`  

The index of the section whose item count you want. This index is 0-based.

## Return Value

The number of items in the section.

## Discussion

Use this method to get the number of items currently displayed by the collection view for the specified section. Do not call the methods of the data source to get this information.

## See Also

### Getting the State of the Collection View

var numberOfSections: Int

The number of sections in the collection view.

