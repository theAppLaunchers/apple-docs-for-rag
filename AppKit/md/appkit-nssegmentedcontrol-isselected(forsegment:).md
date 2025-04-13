

- AppKit
- NSSegmentedControl
-  isSelected(forSegment:) 

Instance Method

# isSelected(forSegment:)

Returns a Boolean value indicating whether the specified segment is selected.

macOS

``` source
@MainActor
func isSelected(forSegment segment: Int) -> Bool
```

## Parameters 

`segment`  

The index of the segment whose selection state you want to get. This method raises an exception (rangeException) if the index is out of bounds.

## Return Value

true if the segment is selected; otherwise, false.

## See Also

### Managing the Selected Segment

var selectedSegment: Int

The index of the selected segment of the control, or `-1` if no segment is selected.

var indexOfSelectedItem: Int

func selectSegment(withTag: Int) -> Bool

Selects the segment with the specified tag.

func setSelected(Bool, forSegment: Int)

Sets the selection state of the specified segment.

var selectedSegmentBezelColor: NSColor?

The color of the selected segment’s bezel, in appearances that support it.

var doubleValueForSelectedSegment: Double

When the tracking mode for the control is set to use a momentary accelerator, returns a value for the selected segment.

