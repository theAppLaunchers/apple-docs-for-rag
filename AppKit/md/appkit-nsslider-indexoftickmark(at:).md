

- AppKit
- NSSlider
-  indexOfTickMark(at:) 

Instance Method

# indexOfTickMark(at:)

Returns the index of the tick mark closest to the location of the slider represented by the given point.

macOS

``` source
@MainActor
func indexOfTickMark(at point: NSPoint) -> Int
```

## Parameters 

`point`  

The point representing the location for which to retrieve the tick mark.

## Return Value

The index of the tick mark closest to the location specified by `point`. If `point` is not within the bounding rectangle (plus an extra pixel of space) of any tick mark, the method returns `NSNotFound`.

## Discussion

In its implementation of this method, the receiving `NSSlider` instance invokes the method of the same name of its `NSSliderCell` instance. This method invokes rectOfTickMark(at:) for each tick mark on the slider until it finds a tick mark containing the point.

## See Also

### Managing Tick Marks

var allowsTickMarkValuesOnly: Bool

A Boolean value that indicates whether the slider fixes its values to those values represented by its tick marks.

func closestTickMarkValue(toValue: Double) -> Double

Returns the value of the tick mark closest to the specified value.

var numberOfTickMarks: Int

The number of tick marks associated with the slider.

func rectOfTickMark(at: Int) -> NSRect

Returns the bounding rectangle of the tick mark at the given index.

var tickMarkPosition: NSSlider.TickMarkPosition

Determines where the slider’s tick marks are displayed.

enum TickMarkPosition

The position where a linear slider’s tick marks appear (above, below, leading, or trailing).

func tickMarkValue(at: Int) -> Double

Returns the slider’s value represented by the tick mark at the specified index.

