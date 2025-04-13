

- AppKit
- NSMatrix
-  deselectAllCells() 

Instance Method

# deselectAllCells()

Deselects all cells in the receiver and, if necessary, redisplays the receiver.

macOS

``` source
@MainActor
func deselectAllCells()
```

## Discussion

If the selection mode is `NSRadioModeMatrix` and empty selection is not allowed, this method does nothing.

## See Also

### Related Documentation

var mode: NSMatrix.Mode

The selection mode of the receiver.

var allowsEmptySelection: Bool

A Boolean that indicates whether a radio-mode matrix supports an empty selection.

### Selecting and Deselecting Cells

func selectCell(atRow: Int, column: Int)

Selects the cell at the specified row and column within the receiver.

func selectCell(withTag: Int) -> Bool

Selects the last cell with the given tag.

func selectAll(Any?)

Selects and highlights all cells in the receiver.

var keyCell: NSCell?

The cell that will be clicked when the user presses the Space bar.

func setSelectionFrom(Int, to: Int, anchor: Int, highlight: Bool)

Programmatically selects a range of cells.

func deselectSelectedCell()

Deselects the selected cell or cells.

