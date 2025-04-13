

- Core Text
-  CTFrameGetLineOrigins(\_:\_:\_:) 

Function

# CTFrameGetLineOrigins(\_:\_:\_:)

Copies a range of line origins for a frame.

iOS 3.2+iPadOS 3.2+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func CTFrameGetLineOrigins(
    _ frame: CTFrame,
    _ range: CFRange,
    _ origins: UnsafeMutablePointer
)
```

## Parameters 

`frame`  

The frame whose line origin array is copied.

`range`  

The range of line origins you wish to copy. If the length of the range is 0, then the copy operation continues from the start index of the range to the last line origin.

`origins`  

The buffer to which the origins are copied. The buffer must have at least as many elements as specified by range’s length. Each CGPoint in this array is the origin of the corresponding line in the array of lines returned by CTFrameGetLines(_:) relative to the origin of the path’s bounding box, which can be obtained from `CGPathGetPathBoundingBox`.

## Discussion

This function copies a range of CGPoint structures into the `origins` buffer. The maximum number of line origins this function will copy into the `origins` buffer is the count of the array of lines (the length of the `range` parameter).

### Special Considerations

In versions of macOS prior to 10.7 and versions of iOS prior to 4.2, this function may function unpredictably if the frame is not rectangular.

## See Also

### Getting Lines

func CTFrameGetLines(CTFrame) -> CFArray

Returns an array of lines stored in the frame.

