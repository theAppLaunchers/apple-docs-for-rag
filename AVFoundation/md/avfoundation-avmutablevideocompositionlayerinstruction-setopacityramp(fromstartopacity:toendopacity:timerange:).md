

- AVFoundation
- AVMutableVideoCompositionLayerInstruction
-  setOpacityRamp(fromStartOpacity:toEndOpacity:timeRange:) 

Instance Method

# setOpacityRamp(fromStartOpacity:toEndOpacity:timeRange:)

Sets an opacity ramp to apply during a specified time range.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+

``` source
func setOpacityRamp(
    fromStartOpacity startOpacity: Float,
    toEndOpacity endOpacity: Float,
    timeRange: CMTimeRange
)
```

## Parameters 

`startOpacity`  

The opacity to be applied at the start time of `timeRange`. The value must be between `0.0` and `1.0`.

`endOpacity`  

The opacity to be applied at the end time of `timeRange`. The value must be between `0.0` and `1.0`.

`timeRange`  

The time range over which the value of the opacity is interpolated between `startOpacity` and `endOpacity`.

## Discussion

During an opacity ramp, opacity is computed using a linear interpolation. Before the first time for which an opacity is set, the opacity is held constant at `1.0`; after the last specified time, the opacity is held constant at the last value.

## See Also

### Managing Properties

func setOpacity(Float, at: CMTime)

Sets the opacity value at a specific time within the time range of the instruction.

func setTransform(CGAffineTransform, at: CMTime)

Sets the transform value at a time within the time range of the instruction.

func setTransformRamp(fromStart: CGAffineTransform, toEnd: CGAffineTransform, timeRange: CMTimeRange)

Sets a transform ramp to apply during a given time range.

