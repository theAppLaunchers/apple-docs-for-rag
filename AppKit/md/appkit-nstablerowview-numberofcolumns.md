

- AppKit
- NSTableRowView
-  numberOfColumns 

Instance Property

# numberOfColumns

Returns the number of columns represented by views in the table row view.

macOS 10.7+

``` source
@MainActor
var numberOfColumns: Int { get }
```

## Discussion

The number of columns may not be equal to the number of columns in the enclosing NSTableView, if this row view is a group style and has a single view that spans the entire width of the row.

## See Also

### Row Grouping

var isGroupRowStyle: Bool

Specifies whether this row view is a group row.

