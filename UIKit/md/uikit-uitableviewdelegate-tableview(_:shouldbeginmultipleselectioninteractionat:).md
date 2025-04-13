

- UIKit
- UITableViewDelegate
-  tableView(\_:shouldBeginMultipleSelectionInteractionAt:) 

Instance Method

# tableView(\_:shouldBeginMultipleSelectionInteractionAt:)

Asks the delegate whether the user can use a two-finger pan gesture to select multiple items in a table view.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
@MainActor
optional func tableView(
    _ tableView: UITableView,
    shouldBeginMultipleSelectionInteractionAt indexPath: IndexPath
) -> Bool
```

## Parameters 

`tableView`  

The table view calling this method.

`indexPath`  

The index path of the row that the user touched to start the two-finger pan gesture.

## Return Value

true to allow the user to select multiple rows using a two-finger pan gesture; otherwise, false to disable the behavior. The default value is false.

## Discussion

When the system recognizes a two-finger pan gesture, it calls this method before it sets isEditing to true. If you return true from this method, the user can select multiple rows using a two-finger pan gesture.

In macOS, the system calls this method when a user attempts to select multiple rows by holding a modifier key and clicking additional rows to select them.

To support multiple selection using the two-finger pan gesture (in iOS) or modifier keys (in macOS), set the allowsMultipleSelectionDuringEditing property to true when you configure the table view.

## See Also

### Responding to row selections

Handling row selection in a table view

Detect when a user taps a table view cell so your app can take the next indicated action.

Selecting multiple items with a two-finger pan gesture

Accelerate user selection of multiple items using the multiselect gesture on table and collection views.

func tableView(UITableView, willSelectRowAt: IndexPath) -> IndexPath?

Tells the delegate a row is about to be selected.

func tableView(UITableView, didSelectRowAt: IndexPath)

Tells the delegate a row is selected.

func tableView(UITableView, willDeselectRowAt: IndexPath) -> IndexPath?

Tells the delegate that a specified row is about to be deselected.

func tableView(UITableView, didDeselectRowAt: IndexPath)

Tells the delegate that the specified row is now deselected.

func tableView(UITableView, didBeginMultipleSelectionInteractionAt: IndexPath)

Tells the delegate when the user starts using a two-finger pan gesture to select multiple rows in a table view.

func tableViewDidEndMultipleSelectionInteraction(UITableView)

Tells the delegate when the user stops using a two-finger pan gesture to select multiple rows in a table view.

