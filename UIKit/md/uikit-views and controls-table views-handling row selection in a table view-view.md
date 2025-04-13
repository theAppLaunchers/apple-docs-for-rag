

- UIKit
- Views and controls
- Table views
-  Handling row selection in a table view 

Article

# Handling row selection in a table view

Detect when a user taps a table view cell so your app can take the next indicated action.

## Overview

When a user taps a row of a table view, an action of some kind usually follows, such as another view sliding into place, or the row indicating the selected state with a checkmark. In order for your app to perform the action, it must know when the user taps the row and respond accordingly.

### Configure row selection behavior

Use the following properties to configure how row selection behaves in a table view:

allowsSelection  
Determines whether users can select a row when the table isn’t in editing mode. The default is true.

allowsMultipleSelection  
Determines whether users can select more than one row when the table isn’t in editing mode. The default is false.

allowsSelectionDuringEditing  
Determines whether user can select a row while the table view is in editing mode. The default is false.

allowsMultipleSelectionDuringEditing  
Determines whether users can select a more than one row while in editing mode. The default is false.

### Respond to row selections

When the user taps a row, the table view calls the delegate method tableView(_:didSelectRowAt:). At this point, your app performs the action, such as displaying the details of the selected hiking trail:

```
func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
    let selectedTrail = trails[indexPath.row]

    if let viewController = storyboard?.instantiateViewController(identifier: "TrailViewController") as? TrailViewController {
        viewController.trail = selectedTrail
        navigationController?.pushViewController(viewController, animated: true)
    }
}
```

If you respond to the cell selection by pushing a new view controller onto the navigation stack, deselect the cell when the view controller pops off the stack. If you’re using a UITableViewController to display a table view, you get the behavior by setting the clearsSelectionOnViewWillAppear property to true. Otherwise, you can clear the selection in your view controller’s viewWillAppear(_:) method:

```
override func viewWillAppear(_ animated: Bool) {
    super.viewWillAppear(animated)
    if let selectedIndexPath = tableView.indexPathForSelectedRow {
        tableView.deselectRow(at: selectedIndexPath, animated: animated)
    }
}
```

If the row displays the detail button accessory view and the user taps it, the table view calls the tableView(_:accessoryButtonTappedForRowWith:) method instead of calling the tableView(_:didSelectRowAt:) method. To learn more about accessory views, see Configuring the cells for your table.

### Select a row programmatically

The selection of a row may originate within the app itself rather than from a tap in the table view. For example, a user might add a new person to an address book, then return to the list of contacts. After returning to the contact list, the app scrolls the list to show the row of the newly added person. In this situation, use the table view method selectRow(at:animated:scrollPosition:) to select and scroll to the new row.

Note

Selecting a row programmatically doesn’t call the delegate methods tableView(_:willSelectRowAt:) or tableView(_:didSelectRowAt:), nor does it send selectionDidChangeNotification notifications to observers.

### Manage selection lists

You can also use cell selection to maintain inclusive and exclusive lists of selected items. An inclusive list can have one or more selected items while an exclusive list has at most one.

When providing a selection list in your app, don’t use the cell’s selected state to indicate the state of the item. Instead, display a checkmark or an accessory view. To indicate the state using a checkmark, implement the tableView(_:didSelectRowAt:) delegate method, then deselect the cell with deselectRow(at:animated:), followed by setting the cell’s accessoryType property to UITableViewCell.AccessoryType.checkmark.

For example, an app for backpackers may let users create a packing list—an inclusive list of camping gear like sleeping bags and tents. When the user taps an item to indicate that they packed that piece of gear, the app unselects the row, updates the item’s data model, and displays a checkmark in the row for packed items. Tapping the item again marks the item as unpacked and removes the checkmark. Here’s an example:

```
func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
    // Unselect the row, and instead, show the state with a checkmark.
    tableView.deselectRow(at: indexPath, animated: false)

    guard let cell = tableView.cellForRow(at: indexPath) else { return }

    // Update the selected item to indicate whether the user packed it or not.
    let item = packingList[indexPath.row]
    let newItem = PackingItem(name: item.name, isPacked: !item.isPacked)
    packingList.remove(at: indexPath.row)
    packingList.insert(newItem, at: indexPath.row)

    // Show a check mark next to packed items.
    if newItem.isPacked {
        cell.accessoryType = .checkmark
    } else {
        cell.accessoryType = .none
    }
}
```

Managing an exclusive list is similar. Deselect the row and display a checkmark or an accessory view to indicate the selected state. But unlike an inclusive list, limit the exclusive list to only one selected item at a time.

For instance, the backpacker’s app may let users filter the list of hiking trails based on a single difficulty level: easy, moderate, and hard. With this kind of exclusive list, the app must remove the checkmark from the previous selection, and display a checkmark for the current selection. The app must also remember which item is the currently selected item. For example:

```
func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
    // Unselect the row.
    tableView.deselectRow(at: indexPath, animated: false)

    // Did the user tap on a selected filter item? If so, do nothing.
    let selectedFilterRow = selectedFilters[indexPath.section]
    if selectedFilterRow == indexPath.row {
        return
    }

    // Remove the checkmark from the previously selected filter item.
    if let previousCell = tableView.cellForRow(at: IndexPath(row: selectedFilterRow, section: indexPath.section)) {
        previousCell.accessoryType = .none
    }

    // Mark the newly selected filter item with a checkmark.
    if let cell = tableView.cellForRow(at: indexPath) {
        cell.accessoryType = .checkmark
    }

    // Remember this selected filter item.
    selectedFilters[indexPath.section] = indexPath.row
}
```

## See Also

### Selection management

Selecting multiple items with a two-finger pan gesture

Accelerate user selection of multiple items using the multiselect gesture on table and collection views.

