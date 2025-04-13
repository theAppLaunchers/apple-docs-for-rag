

- AppKit
-  NSBrowserDelegate 

Protocol

# NSBrowserDelegate

A set of methods that a browser delegate implements to manage selection, scrolling, sizing, and other behavior.

macOS

``` source
protocol NSBrowserDelegate : NSObjectProtocol
```

## Topics

### Getting Browser Information

func browser(NSBrowser, isColumnValid: Int) -> Bool

Returns whether the contents of the specified column are valid.

func browser(NSBrowser, numberOfRowsInColumn: Int) -> Int

Returns the number of rows of data in the specified column.

func browser(NSBrowser, numberOfChildrenOfItem: Any?) -> Int

Asks the delegate for the number of children the given item has.

func browser(NSBrowser, titleOfColumn: Int) -> String?

Asks the delegate for the title to display above the specified column.

### Managing Selection Behavior

func browser(NSBrowser, shouldTypeSelectFor: NSEvent, withCurrentSearch: String?) -> Bool

Sent to the delegate to determine whether keyboard-based selection (type select) for a given event and search string should proceed.

func browser(NSBrowser, typeSelectStringForRow: Int, inColumn: Int) -> String?

Sent to the delegate to get the keyboard-based selection (type select) string for the specified row and column.

func browser(NSBrowser, nextTypeSelectMatchFromRow: Int, toRow: Int, inColumn: Int, for: String?) -> Int

Sent to the delegate to customize a browser’s keyboard-based selection (type select) behavior.

### Managing Selection

func browser(NSBrowser, selectCellWith: String, inColumn: Int) -> Bool

Asks the delegate to select the cell with the given title in the specified column.

func browser(NSBrowser, selectRow: Int, inColumn: Int) -> Bool

Asks the delegate to select the cell at the specified row and column location.

func browser(NSBrowser, selectionIndexesForProposedSelection: IndexSet, inColumn: Int) -> IndexSet

Asks the delegate for a set of indexes to select when the user changes the selection in the browser with the keyboard or mouse.

### Accessing Components

func browser(NSBrowser, child: Int, ofItem: Any?) -> Any

Asks the delegate to return the child of the specified item at the specified index.

func browser(NSBrowser, isLeafItem: Any?) -> Bool

Asks the delegate whether the specified item is a leaf item (an item that cannot be expanded).

func browser(NSBrowser, shouldEditItem: Any?) -> Bool

Asks the delegate whether the browser may start an editing session for the specified item.

func browser(NSBrowser, objectValueForItem: Any?) -> Any?

Returns the object that the specified item uses to draw its contents.

func browser(NSBrowser, setObjectValue: Any?, forItem: Any?)

Sets the object that the specified item uses to draw its contents to the specified object.

func rootItem(for: NSBrowser) -> Any?

Asks the delegate to return the root item of the browser.

func browser(NSBrowser, previewViewControllerForLeafItem: Any) -> NSViewController?

Asks the delegate for a controller that provides a preview column for the specified leaf item.

func browser(NSBrowser, headerViewControllerForItem: Any?) -> NSViewController?

Asks the delegate for a controller that provides a header view for the specified column item.

### Managing Columns

func browser(NSBrowser, createRowsForColumn: Int, in: NSMatrix)

Creates a row in the given matrix for each row of data in the specified column of the browser.

func browser(NSBrowser, willDisplayCell: Any, atRow: Int, column: Int)

Gives the delegate the opportunity to modify the specified cell at the given row and column location before the browser displays it.

func browser(NSBrowser, didChangeLastColumn: Int, toColumn: Int)

Tells the delegate that the browser’s last column changed.

### Scrolling

func browserWillScroll(NSBrowser)

Notifies the delegate when the browser will scroll.

func browserDidScroll(NSBrowser)

Notifies the delegate when the browser has scrolled.

### Dragging

func browser(NSBrowser, canDragRowsWith: IndexSet, inColumn: Int, with: NSEvent) -> Bool

Sent to the delegate to determine whether the browser can attempt to initiate a drag of the specified rows for the specified event.

func browser(NSBrowser, draggingImageForRowsWith: IndexSet, inColumn: Int, with: NSEvent, offset: NSPointPointer) -> NSImage?

Sent to the delegate to obtain an image to represent dragged rows during a drag operation on a browser.

func browser(NSBrowser, validateDrop: any NSDraggingInfo, proposedRow: UnsafeMutablePointer&lt;Int>, column: UnsafeMutablePointer&lt;Int>, dropOperation: UnsafeMutablePointer&lt;NSBrowser.DropOperation>) -> NSDragOperation

Sent to the delegate during a dragging session to determine whether a drop should be accepted and to obtain the drop location. This method is required for a browser to be a drag destination.

func browser(NSBrowser, acceptDrop: any NSDraggingInfo, atRow: Int, column: Int, dropOperation: NSBrowser.DropOperation) -> Bool

Sent to the delegate during a dragging session to determine whether to accept the drop.

func browser(NSBrowser, writeRowsWith: IndexSet, inColumn: Int, to: NSPasteboard) -> Bool

Determines whether a drag operation can proceed. This method is required for a browser to be a drag source.

func browser(NSBrowser, namesOfPromisedFilesDroppedAtDestination: URL, forDraggedRowsWith: IndexSet, inColumn: Int) -> [String]

Implements file promise drag operations.

Deprecated

### Sizing

func browser(NSBrowser, shouldSizeColumn: Int, forUserResize: Bool, toWidth: CGFloat) -> CGFloat

Used to determine a column’s initial size.

func browser(NSBrowser, sizeToFitWidthOfColumn: Int) -> CGFloat

Returns the ideal width for a column.

func browserColumnConfigurationDidChange(Notification)

Used by clients to implement their own column width persistence.

func browser(NSBrowser, heightOfRow: Int, inColumn: Int) -> CGFloat

Specifies the height of the specified row in the specified column.

### Displaying Cell Content

func browser(NSBrowser, shouldShowCellExpansionForRow: Int, column: Int) -> Bool

Invoked to allow the delegate to control cell expansion for a specific row and column.

## Relationships

### Inherits From

- NSObjectProtocol

