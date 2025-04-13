

- AVFoundation
- AVMutableVideoCompositionLayerInstruction
-  setOpacity(\_:at:) 

Instance Method

# setOpacity(\_:at:)

Sets the opacity value at a specific time within the time range of the instruction.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+

``` source
func setOpacity(
    _ opacity: Float,
    at time: CMTime
)
```

## Parameters 

`opacity`  

The opacity to be applied at `time`. The value must be between `0.0` and `1.0`.

`time`  

A time value within the time range of the composition instruction.

## Discussion

Sets a fixed opacity to apply from the specified time until the next time at which an opacity is set; this is the same as setting a flat ramp for that time range. Before the first time for which an opacity is set, the opacity is held constant at `1.0`; after the last specified time, the opacity is held constant at the last value.

## See Also

### Managing Properties

func setOpacityRamp(fromStartOpacity: Float, toEndOpacity: Float, timeRange: CMTimeRange)

Sets an opacity ramp to apply during a specified time range.

func setTransform(CGAffineTransform, at: CMTime)

Sets the transform value at a time within the time range of the instruction.

func setTransformRamp(fromStart: CGAffineTransform, toEnd: CGAffineTransform, timeRange: CMTimeRange)

Sets a transform ramp to apply during a given time range.

