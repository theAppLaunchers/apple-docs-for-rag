

- Notification Center
- NCWidgetListViewDelegate
-  widgetListPerformAddAction(\_:) Deprecated

Instance Method

# widgetListPerformAddAction(\_:)

Asks the delegate to perform an action when the Add (+) button is clicked.

macOS 10.10–11.0Deprecated

``` source
optional func widgetListPerformAddAction(_ list: NCWidgetListViewController)
```

Deprecated

Use WidgetKit instead.

## Parameters 

`list`  

The widget’s list view controller.

## Discussion

When a widget’s list is in editing mode, the list view controller can display an Add (+) button. The button’s action calls `widgetListPerformAddAction:` in the delegate.

If you want to display the default search view in the add action, you can use the `presentViewControllerInWidget:` method of `NSViewController` to present an NCWidgetSearchViewController instance in the widget’s principal view controller.

## See Also

### Adding and Deleting Rows

func widgetList(NCWidgetListViewController, didRemoveRow: Int)

Tells the delegate that the specified row was removed from the list.

Deprecated

func widgetList(NCWidgetListViewController, shouldRemoveRow: Int) -> Bool

Asks the delegate to allow or prohibit the specified row to be removed from the list.

Deprecated

