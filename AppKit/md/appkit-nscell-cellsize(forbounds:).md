

- AppKit
- NSCell
-  cellSize(forBounds:) 

Instance Method

# cellSize(forBounds:)

Returns the minimum size needed to display the receiver, constraining it to the specified rectangle.

macOS

``` source
@MainActor
func cellSize(forBounds rect: NSRect) -> NSSize
```

## Parameters 

`rect`  

The size of the cell, or the size of the `aRect` parameter if the cell is not a text or image cell. If the cell is an image cell but no image has been set, returns `NSZeroSize`.

## Discussion

This method takes into account of the size of the image or text within a certain offset determined by the border type of the cell. If the receiver is of text type, the text is resized to fit within `aRect` (as much as `aRect` is within the bounds of the cell).

To support constraint-based layout, when the content of a custom cell changes in such a way that the return value of this method would change, the cell needs to notify its control of the change by calling the control’s invalidateIntrinsicContentSize(for:) method.

## See Also

### Determining Cell Size

func calcDrawInfo(NSRect)

Recalculates the cell geometry.

var cellSize: NSSize

The minimum size needed to display the cell.

func drawingRect(forBounds: NSRect) -> NSRect

Returns the rectangle within which the receiver draws itself

func imageRect(forBounds: NSRect) -> NSRect

Returns the rectangle in which the receiver draws its image.

func titleRect(forBounds: NSRect) -> NSRect

Returns the rectangle in which the receiver draws its title text.

var controlSize: NSControl.ControlSize

The size of the cell.

