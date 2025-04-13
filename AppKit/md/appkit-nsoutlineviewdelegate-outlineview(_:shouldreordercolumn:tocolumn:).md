

- AppKit
- NSOutlineViewDelegate
-  outlineView(\_:shouldReorderColumn:toColumn:) 

Instance Method

# outlineView(\_:shouldReorderColumn:toColumn:)

Sent to the delegate to allow or prohibit the specified column to be dragged to a new location.

macOS 10.6+

``` source
@MainActor
optional func outlineView(
    _ outlineView: NSOutlineView,
    shouldReorderColumn columnIndex: Int,
    toColumn newColumnIndex: Int
) -> Bool
```

## Parameters 

`outlineView`  

The outline view that sent the message.

`columnIndex`  

The index of the column being dragged.

`newColumnIndex`  

The proposed target index of the column.

## Return Value

true if the column reordering should be allowed, otherwise false.

## Discussion

When a column is initially dragged by the user, the delegate is first called with a `newColumnIndex` value of `-1`. Returning false will disallow that column from being reordered at all. Returning true allows it to be reordered, and the delegate will be called again when the column reaches a new location.

The actual `NSTableColumn` instance can be retrieved from the tableColumns array.

If this method is not implemented, all columns are considered reorderable.

