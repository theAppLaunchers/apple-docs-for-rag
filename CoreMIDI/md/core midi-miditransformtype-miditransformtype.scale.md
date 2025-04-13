

- Core MIDI
- MIDITransformType
-  MIDITransformType.scale 

Case

# MIDITransformType.scale

A transform that multiplies by the specified parameter value.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
case scale
```

## Discussion

Specify the parameter value in fixed point format: `bbbb.bbbb bbbb bbbb`

## See Also

### Transform Types

case none

No transformation.

case filterOut

A transformation that filters out an event type.

case mapControl

A transformation that changes a specified control number to a supplied parameter value.

case add

A transform that adds a parameter value.

case minValue

A transform that sets the minimum value to the specified parameter value.

case maxValue

A transform that sets the maximum value to the specified parameter value.

case mapValue

A transform that maps one value to another.

