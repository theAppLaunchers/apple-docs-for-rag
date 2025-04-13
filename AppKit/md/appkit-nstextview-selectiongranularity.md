

- AppKit
- NSTextView
-  selectionGranularity 

Instance Property

# selectionGranularity

The selection granularity for subsequent extension of a selection.

macOS

``` source
@MainActor
var selectionGranularity: NSSelectionGranularity { get set }
```

## Discussion

Selection granularity is used to determine how the selection is modified when the user Shift-clicks or drags the mouse after a double or triple click. For example, if the user selects a word by double-clicking, the selection granularity is set to `NSSelectByWord`. Subsequent Shift-clicks then extend the selection by words.

Selection granularity is reset to `NSSelectByCharacter` whenever the selection is set. You should always set the selection granularity after setting the selection.

## See Also

### Managing the selection

var selectedRanges: [NSValue]

An array containing the ranges of characters selected in the receiver’s layout manager.

func setSelectedRange(NSRange)

Selects the specified range of characters in response to user action.

func setSelectedRange(NSRange, affinity: NSSelectionAffinity, stillSelecting: Bool)

Sets the selection to a range of characters in response to user action.

func setSelectedRanges([NSValue], affinity: NSSelectionAffinity, stillSelecting: Bool)

Sets the selection to the characters in an array of ranges in response to user action.

var selectionAffinity: NSSelectionAffinity

The preferred direction of selection.

var insertionPointColor: NSColor!

The color of the insertion point.

func updateInsertionPointStateAndRestartTimer(Bool)

Updates the insertion point’s location and optionally restarts the blinking cursor timer.

var selectedTextAttributes: [NSAttributedString.Key : Any]

The attributes used to indicate the selection.

var markedTextAttributes: [NSAttributedString.Key : Any]?

The attributes used to draw marked text.

var linkTextAttributes: [NSAttributedString.Key : Any]?

The attributes used to draw the onscreen presentation of link text.

func characterIndexForInsertion(at: NSPoint) -> Int

Returns a character index appropriate for placing a zero-length selection for an insertion point associated with the mouse at the given point.

func updateCandidates()

