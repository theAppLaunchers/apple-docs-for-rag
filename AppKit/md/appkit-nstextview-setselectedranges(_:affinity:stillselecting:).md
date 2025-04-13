

- AppKit
- NSTextView
-  setSelectedRanges(\_:affinity:stillSelecting:) 

Instance Method

# setSelectedRanges(\_:affinity:stillSelecting:)

Sets the selection to the characters in an array of ranges in response to user action.

macOS

``` source
@MainActor
func setSelectedRanges(
    _ ranges: [NSValue],
    affinity: NSSelectionAffinity,
    stillSelecting stillSelectingFlag: Bool
)
```

## Parameters 

`ranges`  

A non-nil, non-empty array of objects responding to the NSValue `rangeValue` method. The ranges in the `ranges` array must begin and end on glyph boundaries and not split base glyphs and their nonspacing marks.

`affinity`  

The selection affinity for the selection. See selectionAffinity for more information about how affinities work.

`stillSelectingFlag`  

true to behave appropriately for a continuing selection where the user is still dragging the mouse, false otherwise. If true, the receiver doesn’t send notifications or remove the marking from its marked text. If false, the receiver posts an didChangeSelectionNotification to the default notification center and removes the marking from marked text if the new selection is greater than the marked region.

## Discussion

This method also resets the selection granularity to `NSSelectByCharacter`.

## See Also

### Managing the selection

var selectedRanges: [NSValue]

An array containing the ranges of characters selected in the receiver’s layout manager.

func setSelectedRange(NSRange)

Selects the specified range of characters in response to user action.

func setSelectedRange(NSRange, affinity: NSSelectionAffinity, stillSelecting: Bool)

Sets the selection to a range of characters in response to user action.

var selectionAffinity: NSSelectionAffinity

The preferred direction of selection.

var selectionGranularity: NSSelectionGranularity

The selection granularity for subsequent extension of a selection.

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

