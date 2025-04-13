

- Notification Center
-  NCWidgetListViewDelegate Deprecated

Protocol

# NCWidgetListViewDelegate

The interface for handling content display and editing in the list view of a macOS Today widget.

macOS 10.10–11.0Deprecated

``` source
protocol NCWidgetListViewDelegate : NSObjectProtocol
```

Deprecated

Use WidgetKit instead.

## Overview

The `NCWidgetListViewDelegate` protocol defines methods that handle content display and editing in the list view of a Today widget. The delegate of an NCWidgetListViewController must adopt the `NCWidgetListViewDelegate` protocol.

The single required method in the protocol, widgetList(_:viewControllerForRow:), creates a view controller for the contents of one row in the widget’s list view. Optional methods in the `NCWidgetListViewDelegate` protocol support editing actions, such as adding a new list item and reordering or deleting list rows.

## Topics

### Creating a Content View Controller

func widgetList(NCWidgetListViewController, viewControllerForRow: Int) -> NSViewController

Asks the delegate for a content view controller for the specified row.

**Required**

### Adding and Deleting Rows

func widgetList(NCWidgetListViewController, didRemoveRow: Int)

Tells the delegate that the specified row was removed from the list.

func widgetList(NCWidgetListViewController, shouldRemoveRow: Int) -> Bool

Asks the delegate to allow or prohibit the specified row to be removed from the list.

func widgetListPerformAddAction(NCWidgetListViewController)

Asks the delegate to perform an action when the Add (+) button is clicked.

### Reordering List Rows

func widgetList(NCWidgetListViewController, didReorderRow: Int, toRow: Int)

Tells the delegate that the specified row was moved to a new location.

func widgetList(NCWidgetListViewController, shouldReorderRow: Int) -> Bool

Asks the delegate to allow or prohibit the specified row to be moved to a new location in the list.

## Relationships

### Inherits From

- NSObjectProtocol

## See Also

### Displaying and Editing List Content

var delegate: (any NCWidgetListViewDelegate)?

The list view controller’s delegate or `nil` if the receiver doesn’t have a delegate.

Deprecated

