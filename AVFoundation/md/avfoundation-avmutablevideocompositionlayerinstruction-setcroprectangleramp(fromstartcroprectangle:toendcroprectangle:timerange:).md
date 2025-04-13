

- AVFoundation
- AVMutableVideoCompositionLayerInstruction
-  setCropRectangleRamp(fromStartCropRectangle:toEndCropRectangle:timeRange:) 

Instance Method

# setCropRectangleRamp(fromStartCropRectangle:toEndCropRectangle:timeRange:)

Sets a crop rectangle ramp to apply during the specified time range.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.0+visionOS 1.0+

``` source
func setCropRectangleRamp(
    fromStartCropRectangle startCropRectangle: CGRect,
    toEndCropRectangle endCropRectangle: CGRect,
    timeRange: CMTimeRange
)
```

## Parameters 

`startCropRectangle`  

The crop rectangle to be applied at the starting time of the `timeRange`.

`endCropRectangle`  

The crop rectangle to be applied at the end time of the timeRange.

`timeRange`  

The time range over which the value of the opacity is interpolated between `startCropRectangle` and `endCropRectangle`.

## Discussion

The origin of the crop rectangle is the top-left corner of the buffer clean aperture rectangle. The crop rectangle is defined in square pixel space, that is, without taking the pixel aspect ratio into account. Crop rectangles extending outside of the clean aperture, are cropped to the clean aperture.

During a crop rectangle ramp, the rectangle is interpolated between the values set at the ramp’s start time and end time. When the starting or ending rectangle is empty, interpolations take into account the origin and size of the empty rectangle.

Before the first specified time for which a crop rectangle is set, the crop rectangle is held constant to CGRectInfinite and after the last time for which a crop rectangle is set, the crop rectangle is held constant at that last value.

## See Also

### Setting Crop Rectangle Values

func setCropRectangle(CGRect, at: CMTime)

Sets the crop rectangle value at a time within the time range of the instruction.

