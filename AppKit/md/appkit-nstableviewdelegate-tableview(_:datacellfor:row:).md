

- AppKit
- NSTableViewDelegate
-  tableView(\_:dataCellFor:row:) 

Instance Method

# tableView(\_:dataCellFor:row:)

Asks the delegate for a custom data cell for the specified row and column.

macOS 10.5+

``` source
@MainActor
optional func tableView(
    _ tableView: NSTableView,
    dataCellFor tableColumn: NSTableColumn?,
    row: Int
) -> NSCell?
```

## Parameters 

`tableView`  

The table view that sent the message.

`tableColumn`  

The table column.

`row`  

The row index.

## Return Value

An NSCell subclass that is used for the specified `row` and `tableColumn`. The returned cell must properly implement `copyWithZone:`.

## Discussion

A different data cell can be returned for any particular table column and row, or a cell that will be used for the entire row (that is, a full width cell).

If `tableColumn` is non-`nil`, you should return a cell (generally as the result of sending `tableColumn` a dataCell(forRow:) message).

While each row is being drawn, this method is first called with a `tableColumn` value of `nil` to allow you to return a group cell—that is, a cell that will be used to draw the entire row. If you return a cell when `tableColumn` is `nil`, all implemented datasource and delegate methods must be prepared to handle a `nil` table column value. If you don’t return a cell, this method is called once for each `tableColumn` in `tableView`.

Note

This method is only valid for NSCell-based table views.

## See Also

### Providing cells for rows and columns

func tableView(NSTableView, willDisplayCell: Any, for: NSTableColumn?, row: Int)

Tells the delegate that the table view will display the specified cell at the specified row and column.

func tableView(NSTableView, shouldShowCellExpansionFor: NSTableColumn?, row: Int) -> Bool

Asks the delegate if an expansion tooltip should be displayed for a specific row and column.

func tableView(NSTableView, toolTipFor: NSCell, rect: NSRectPointer, tableColumn: NSTableColumn?, row: Int, mouseLocation: NSPoint) -> String

Asks the delegate for a string to display in a tooltip for the specified cell in the column and row.

