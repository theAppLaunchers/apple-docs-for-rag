

- UIKit
- UITableView
-  separatorInset 

Instance Property

# separatorInset

The default inset of cell separators.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
var separatorInset: UIEdgeInsets { get set }
```

## Discussion

In iOS 7 and later, cell separators don’t extend all the way to the edge of the table view. This property sets the default inset for all cells in the table, much as rowHeight sets the default height for cells. It’s also used for managing the “extra” separators drawn at the bottom of plain style tables.

For example, to specify a table view where the default left separator inset is 3 points and the default right separator inset is 11, you’d write:

```
tableView.separatorInset = UIEdgeInsetsMake(0, 3, 0, 11);
```

If every cell in a table contains an image view of the same size, by default iOS vertically aligns the leading edge of all separators. In a table that mixes text-only cells with cells that contain image views, you can use the separatorInset property to ensure that the separators are vertically aligned.

In a right-to-left user interface, an inset that you set using the separatorInset property automatically flips its left and right measurements.

### Special considerations

Only left and right insets are honored. In a right-to-left user interface, the inset measurements are automatically flipped.

## See Also

### Customizing the separator appearance

var separatorStyle: UITableViewCell.SeparatorStyle

The style for table cells to use as separators.

enum SeparatorStyle

The style for cells to use as separators.

var separatorColor: UIColor?

The color of separator rows in the table view.

var separatorEffect: UIVisualEffect?

The effect to apply to table separators.

var separatorInsetReference: UITableView.SeparatorInsetReference

An indicator of how to interpret the separator inset value.

enum SeparatorInsetReference

Constants that indicate how to interpret the separator inset value of a table view.

