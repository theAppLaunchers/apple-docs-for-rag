

- AppKit
- NSOutlineViewDelegate
-  outlineView(\_:typeSelectStringFor:item:) 

Instance Method

# outlineView(\_:typeSelectStringFor:item:)

Returns the string that is used for type selection for a given column and item.

macOS 10.5+

``` source
@MainActor
optional func outlineView(
    _ outlineView: NSOutlineView,
    typeSelectStringFor tableColumn: NSTableColumn?,
    item: Any
) -> String?
```

## Parameters 

`outlineView`  

The outline view that sent the message.

`tableColumn`  

A table column in the outline view.

`item`  

An item in the outline view.

## Return Value

The string that is used for type selection. You may want to change what is searched for based on what is displayed, or simply return nil for that row and/or column to not be searched

## Discussion

Implement this method if you want to control the string that is used for type selection. You may want to change what is searched for based on what is displayed, or simply return `nil` to specify that the given row and/or column should not be searched. By default, all cells with text in them are searched.

The default value when this delegate method is not implemented is:

```
[[outlineView preparedCellAtColumn:tableColumn row:[outlineView rowForItem:item]] stringValue]
```

and you can return this value from the delegate method if you wish.

## See Also

### Supporting Type Select

func outlineView(NSOutlineView, nextTypeSelectMatchFromItem: Any, toItem: Any, for: String) -> Any?

Returns the first item that matches the searchString from within the range of startItem to endItem

func outlineView(NSOutlineView, shouldTypeSelectFor: NSEvent, withCurrentSearch: String?) -> Bool

Returns a Boolean value that indicates whether type select should proceed for a given event and search string.

