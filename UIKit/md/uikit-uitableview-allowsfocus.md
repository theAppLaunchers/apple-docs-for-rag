

- UIKit
- UITableView
-  allowsFocus 

Instance Property

# allowsFocus

A Boolean value that determines whether the table view allows its cells to become focused.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+tvOS 15.0+visionOS 1.0+

``` source
@MainActor
var allowsFocus: Bool { get set }
```

## Discussion

If you implement tableView(_:canFocusRowAt:), its return value takes precedence over the value of this property.

The system determines the default value of this property according to the platform and other properties of the table view.

## See Also

### Working with focus

var allowsFocusDuringEditing: Bool

A Boolean value that determines whether the table view allows its cells to become focused in edit mode.

var selectionFollowsFocus: Bool

A Boolean value that triggers an automatic selection when focus moves to a cell.

var remembersLastFocusedIndexPath: Bool

A Boolean value that indicates whether the table view automatically returns the focus to the cell at the last focused index path.

