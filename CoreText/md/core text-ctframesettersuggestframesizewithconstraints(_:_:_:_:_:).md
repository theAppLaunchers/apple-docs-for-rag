

- Core Text
-  CTFramesetterSuggestFrameSizeWithConstraints(\_:\_:\_:\_:\_:) 

Function

# CTFramesetterSuggestFrameSizeWithConstraints(\_:\_:\_:\_:\_:)

Determines the frame size needed for a string range.

iOS 3.2+iPadOS 3.2+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func CTFramesetterSuggestFrameSizeWithConstraints(
    _ framesetter: CTFramesetter,
    _ stringRange: CFRange,
    _ frameAttributes: CFDictionary?,
    _ constraints: CGSize,
    _ fitRange: UnsafeMutablePointer?
) -> CGSize
```

## Parameters 

`framesetter`  

The framesetter used for measuring the frame size.

`stringRange`  

The string range to which the frame size applies. The string range is a range over the string used to create the framesetter. If the length portion of the range is set to `0`, then the framesetter continues to add lines until it runs out of text or space.

`frameAttributes`  

Additional attributes that control the frame filling process, or `NULL` if there are no such attributes.

`constraints`  

The width and height to which the frame size is constrained. A value of CGFLOAT_MAX for either dimension indicates that it should be treated as unconstrained.

`fitRange`  

On return, contains the range of the string that actually fit in the constrained size.

## Return Value

The actual dimensions for the given string range and constraints.

## Discussion

This function can be used to determine how much space is needed to display a string, optionally by constraining the space along either dimension.

