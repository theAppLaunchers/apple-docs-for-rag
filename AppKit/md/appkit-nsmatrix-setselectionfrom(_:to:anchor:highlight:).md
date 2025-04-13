

- AppKit
- NSMatrix
-  setSelectionFrom(\_:to:anchor:highlight:) 

Instance Method

# setSelectionFrom(\_:to:anchor:highlight:)

Programmatically selects a range of cells.

macOS

``` source
@MainActor
func setSelectionFrom(
    _ startPos: Int,
    to endPos: Int,
    anchor anchorPos: Int,
    highlight lit: Bool
)
```

## Parameters 

`startPos`  

The position of the cell that marks where the user would have pressed the mouse button.

`endPos`  

The position of the cell that marks where the user would have released the mouse button.

`anchorPos`  

The position of the cell to treat as the last cell the user would have selected. To simulate Shift-dragging (continuous selection) `anchorPos` should be the `endPos` used in the last method call. To simulate Command-dragging (discontinuous selection), `anchorPos` should be the same as this method call’s `startPos`.

`lit`  

true if cells selected by this method should be highlighted.

## Discussion

`startPos`, `endPos`, and `anchorPos` are cell positions, counting from 0 at the upper left cell of the receiver, in row order. For example, the third cell in the top row would be number 2.

To simulate dragging without a modifier key, deselecting anything that was selected before, call deselectAllCells() before calling this method.

## See Also

### Related Documentation

var selectedCells: [NSCell]

An array containing all of the matrix’s highlighted cells plus its selected cell.

var isSelectionByRect: Bool

A Boolean that indicates whether the user can select a rectangle of cells in the receiver by dragging the cursor.

### Selecting and Deselecting Cells

func selectCell(atRow: Int, column: Int)

Selects the cell at the specified row and column within the receiver.

func selectCell(withTag: Int) -> Bool

Selects the last cell with the given tag.

func selectAll(Any?)

Selects and highlights all cells in the receiver.

var keyCell: NSCell?

The cell that will be clicked when the user presses the Space bar.

func deselectAllCells()

Deselects all cells in the receiver and, if necessary, redisplays the receiver.

func deselectSelectedCell()

Deselects the selected cell or cells.

