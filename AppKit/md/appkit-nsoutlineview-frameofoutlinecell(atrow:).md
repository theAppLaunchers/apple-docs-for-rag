

- AppKit
- NSOutlineView
-  frameOfOutlineCell(atRow:) 

Instance Method

# frameOfOutlineCell(atRow:)

Returns the frame of the outline cell for a given row.

macOS 10.5+

``` source
@MainActor
func frameOfOutlineCell(atRow row: Int) -> NSRect
```

## Parameters 

`row`  

The index of the row for which to return the frame.

## Return Value

The frame of the outline cell for the row at index `row`, considering the current indentation and the value in the indentationMarkerFollowsCell property. If the row at index `row` is not an expandable row, returns `NSZeroRect`.

## Discussion

You can override this method in a subclass to return a custom frame for the outline button cell. If your override returns an empty rect, no outline cell is drawn for that row. You might do that, for example, so that the disclosure triangle will not be shown for a row that should never be expanded.

