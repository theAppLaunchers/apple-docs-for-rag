

- UIKit
-  UITableViewDelegate 

Protocol

# UITableViewDelegate

Methods for managing selections, configuring section headers and footers, deleting and reordering cells, and performing other actions in a table view.

iOSiPadOSMac CatalysttvOSvisionOS

``` source
@MainActor
protocol UITableViewDelegate : UIScrollViewDelegate
```

## Overview

Use the methods of this protocol to manage the following features:

- Create and manage custom header and footer views.

- Specify custom heights for rows, headers, and footers.

- Provide height estimates for better scrolling support.

- Indent row content.

- Respond to row selections.

- Respond to swipes and other actions in table rows.

- Support editing the table’s content.

The table view specifies rows and sections using IndexPath. For information about how to interpret row and section indexes, see Specify the location of rows and sections.

## Topics

### Configuring rows for the table view

func tableView(UITableView, willDisplay: UITableViewCell, forRowAt: IndexPath)

Tells the delegate the table view is about to draw a cell for a particular row.

func tableView(UITableView, indentationLevelForRowAt: IndexPath) -> Int

Asks the delegate to return the level of indentation for a row in a given section.

func tableView(UITableView, shouldSpringLoadRowAt: IndexPath, with: any UISpringLoadedInteractionContext) -> Bool

Called to let you fine tune the spring-loading behavior of the rows in a table.

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

func tableView(UITableView, shouldBeginMultipleSelectionInteractionAt: IndexPath) -> Bool

Asks the delegate whether the user can use a two-finger pan gesture to select multiple items in a table view.

func tableView(UITableView, didBeginMultipleSelectionInteractionAt: IndexPath)

Tells the delegate when the user starts using a two-finger pan gesture to select multiple rows in a table view.

func tableViewDidEndMultipleSelectionInteraction(UITableView)

Tells the delegate when the user stops using a two-finger pan gesture to select multiple rows in a table view.

### Providing custom header and footer views

func tableView(UITableView, viewForHeaderInSection: Int) -> UIView?

Asks the delegate for a view to display in the header of the specified section of the table view.

func tableView(UITableView, viewForFooterInSection: Int) -> UIView?

Asks the delegate for a view to display in the footer of the specified section of the table view.

func tableView(UITableView, willDisplayHeaderView: UIView, forSection: Int)

Tells the delegate that the table is about to display the header view for the specified section.

func tableView(UITableView, willDisplayFooterView: UIView, forSection: Int)

Tells the delegate that the table is about to display the footer view for the specified section.

### Providing header, footer, and row heights

func tableView(UITableView, heightForRowAt: IndexPath) -> CGFloat

Asks the delegate for the height to use for a row in a specified location.

func tableView(UITableView, heightForHeaderInSection: Int) -> CGFloat

Asks the delegate for the height to use for the header of a particular section.

func tableView(UITableView, heightForFooterInSection: Int) -> CGFloat

Asks the delegate for the height to use for the footer of a particular section.

class let automaticDimension: CGFloat

A constant representing the default value for a given dimension.

### Estimating heights for the table’s content

func tableView(UITableView, estimatedHeightForRowAt: IndexPath) -> CGFloat

Asks the delegate for the estimated height of a row in a specified location.

func tableView(UITableView, estimatedHeightForHeaderInSection: Int) -> CGFloat

Asks the delegate for the estimated height of the header of a particular section.

func tableView(UITableView, estimatedHeightForFooterInSection: Int) -> CGFloat

Asks the delegate for the estimated height of the footer of a particular section.

### Managing accessory views

func tableView(UITableView, accessoryButtonTappedForRowWith: IndexPath)

Tells the delegate that the user tapped the detail button for the specified row.

### Managing context menus

Adding context menus in your app

Provide quick access to useful actions by adding context menus to your iOS app.

func tableView(UITableView, contextMenuConfigurationForRowAt: IndexPath, point: CGPoint) -> UIContextMenuConfiguration?

Returns a context menu configuration for the row at a point.

func tableView(UITableView, previewForDismissingContextMenuWithConfiguration: UIContextMenuConfiguration) -> UITargetedPreview?

Returns the destination view when dismissing a context menu.

func tableView(UITableView, previewForHighlightingContextMenuWithConfiguration: UIContextMenuConfiguration) -> UITargetedPreview?

Returns a view to override the default preview the table view created.

func tableView(UITableView, willDisplayContextMenu: UIContextMenuConfiguration, animator: (any UIContextMenuInteractionAnimating)?)

Informs the delegate when a context menu will appear.

func tableView(UITableView, willEndContextMenuInteraction: UIContextMenuConfiguration, animator: (any UIContextMenuInteractionAnimating)?)

Informs the delegate when a context menu will disappear.

func tableView(UITableView, willPerformPreviewActionForMenuWith: UIContextMenuConfiguration, animator: any UIContextMenuInteractionCommitAnimating)

Informs the delegate when a user triggers a commit by tapping the preview.

### Responding to row actions

func tableView(UITableView, leadingSwipeActionsConfigurationForRowAt: IndexPath) -> UISwipeActionsConfiguration?

Returns the swipe actions to display on the leading edge of the row.

func tableView(UITableView, trailingSwipeActionsConfigurationForRowAt: IndexPath) -> UISwipeActionsConfiguration?

Returns the swipe actions to display on the trailing edge of the row.

func tableView(UITableView, shouldShowMenuForRowAt: IndexPath) -> Bool

Asks the delegate if the editing menu should be shown for a certain row.

Deprecated

func tableView(UITableView, canPerformAction: Selector, forRowAt: IndexPath, withSender: Any?) -> Bool

Asks the delegate if the editing menu should omit the Copy or Paste command for a given row.

Deprecated

func tableView(UITableView, performAction: Selector, forRowAt: IndexPath, withSender: Any?)

Tells the delegate to perform a copy or paste operation on the content of a given row.

Deprecated

func tableView(UITableView, editActionsForRowAt: IndexPath) -> [UITableViewRowAction]?

Asks the delegate for the actions to display in response to a swipe in the specified row.

Deprecated

### Managing table view highlights

func tableView(UITableView, shouldHighlightRowAt: IndexPath) -> Bool

Asks the delegate if the specified row should be highlighted.

func tableView(UITableView, didHighlightRowAt: IndexPath)

Tells the delegate that the specified row was highlighted.

func tableView(UITableView, didUnhighlightRowAt: IndexPath)

Tells the delegate that the highlight was removed from the row at the specified index path.

### Editing table rows

func tableView(UITableView, willBeginEditingRowAt: IndexPath)

Tells the delegate that the table view is about to go into editing mode.

func tableView(UITableView, didEndEditingRowAt: IndexPath?)

Tells the delegate that the table view has left editing mode.

func tableView(UITableView, editingStyleForRowAt: IndexPath) -> UITableViewCell.EditingStyle

Asks the delegate for the editing style of a row at a particular location in a table view.

func tableView(UITableView, titleForDeleteConfirmationButtonForRowAt: IndexPath) -> String?

Changes the default title of the delete-confirmation button.

func tableView(UITableView, shouldIndentWhileEditingRowAt: IndexPath) -> Bool

Asks the delegate whether the background of the specified row should be indented while the table view is in editing mode.

### Reordering table rows

func tableView(UITableView, targetIndexPathForMoveFromRowAt: IndexPath, toProposedIndexPath: IndexPath) -> IndexPath

Asks the delegate to return a new index path to retarget a proposed move of a row.

### Tracking the removal of views

func tableView(UITableView, didEndDisplaying: UITableViewCell, forRowAt: IndexPath)

Tells the delegate that the specified cell was removed from the table.

func tableView(UITableView, didEndDisplayingHeaderView: UIView, forSection: Int)

Tells the delegate that the specified header view was removed from the table.

func tableView(UITableView, didEndDisplayingFooterView: UIView, forSection: Int)

Tells the delegate that the specified footer view was removed from the table.

### Managing table view focus

func tableView(UITableView, canFocusRowAt: IndexPath) -> Bool

Asks the delegate whether the cell at the specified index path is itself focusable.

func tableView(UITableView, shouldUpdateFocusIn: UITableViewFocusUpdateContext) -> Bool

Asks the delegate whether the focus update specified by the context is allowed to occur.

func tableView(UITableView, didUpdateFocusIn: UITableViewFocusUpdateContext, with: UIFocusAnimationCoordinator)

Tells the delegate that a focus update specified by the context has just occurred.

func indexPathForPreferredFocusedView(in: UITableView) -> IndexPath?

Asks the delegate for the table view’s index path for the preferred focused view.

func tableView(UITableView, selectionFollowsFocusForRowAt: IndexPath) -> Bool

Asks the delegate whether to relate selection and focus behavior for the row at the corresponding index path.

### Performing primary actions

func tableView(UITableView, canPerformPrimaryActionForRowAt: IndexPath) -> Bool

Asks the delegate whether to perform a primary action for the row at the specified index path.

func tableView(UITableView, performPrimaryActionForRowAt: IndexPath)

Tells the delegate to perform the primary action for the row at the specified index path.

## Relationships

### Inherits From

- NSObjectProtocol
- UIScrollViewDelegate

### Conforming Types

- UITableViewController

## See Also

### Table management

Estimating the height of a table’s scrolling area

Provide height estimates for your table view’s headers, footers, and rows to ensure that scrolling accurately reflects the size of your content.

class UITableViewController

A view controller that specializes in managing a table view.

class UITableViewFocusUpdateContext

A context object that provides information relevant to a specific focus update from one view to another.

