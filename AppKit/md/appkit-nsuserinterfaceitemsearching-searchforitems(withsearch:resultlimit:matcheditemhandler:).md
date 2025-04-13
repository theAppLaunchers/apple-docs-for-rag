

- AppKit
- NSUserInterfaceItemSearching
-  searchForItems(withSearch:resultLimit:matchedItemHandler:) 

Instance Method

# searchForItems(withSearch:resultLimit:matchedItemHandler:)

Search for the specified items, with the result limit.

macOS

``` source
func searchForItems(
    withSearch searchString: String,
    resultLimit: Int,
    matchedItemHandler handleMatchedItems: @escaping ([Any]) -> Void
)
```

**Required**

## Parameters 

`searchString`  

The string to search for.

`resultLimit`  

The maximum number of results that Spotlight for Help will process. Any results returned beyond this limit will be ignored, but for performance reasons it is better to not exceed it.

`handleMatchedItems`  

The Block used to add results to the search.

The Block takes one argument:

items  
The items to add to the results array. The `handleMatchedItems` block can be invoked from any thread desired. If it is called more than once the additional results will be appended after previous items until the maximum is reached.

## Discussion

Search for items matching the provided search string and return them by calling the matched items block, passing an array of items to append to the help menu. The framework does not care what these items are. They are just used to identify particular search results to other methods in this protocol. Do not assume that this will be called from the main UI thread.

When `searchForItemsWithSearchString:resultLimit:matchedItemHandler:` gets called again, the client should cancel any previous searches in progress for better performance. If not Spotlight for Help will ignore the older results.

## See Also

### Search Help Content

func performAction(forItem: Any)

Invoked when the user selects a search result in Help menu.

