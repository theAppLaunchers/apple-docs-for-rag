

- AppKit
- NSSliderCell
-  closestTickMarkValue(toValue:) 

Instance Method

# closestTickMarkValue(toValue:)

Returns the value of the tick mark closest to the specified value.

macOS

``` source
@MainActor
func closestTickMarkValue(toValue value: Double) -> Double
```

## Parameters 

`value`  

The value for which to obtain the closest tick mark.

## Return Value

The value of the closest tick mark.

## See Also

### Managing Tick Marks

var allowsTickMarkValuesOnly: Bool

A Boolean value indicating whether the receiver fixes its values to those values represented by its tick marks.

func indexOfTickMark(at: NSPoint) -> Int

Returns the index of the tick mark closest to the location of the slider represented by the specified point.

var numberOfTickMarks: Int

The number of tick marks associated with the slider, including the tick marks assigned to the minimum and maximum values.

func rectOfTickMark(at: Int) -> NSRect

Returns the bounding rectangle of the tick mark at the specified index.

var tickMarkPosition: NSSlider.TickMarkPosition

The position of the tick marks relative to the receiver.

func tickMarkValue(at: Int) -> Double

Returns the receiver’s value represented by the tick mark at the specified index.

