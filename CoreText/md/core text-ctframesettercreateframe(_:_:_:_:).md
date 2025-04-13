

- Core Text
-  CTFramesetterCreateFrame(\_:\_:\_:\_:) 

Function

# CTFramesetterCreateFrame(\_:\_:\_:\_:)

Creates an immutable frame using a framesetter.

iOS 3.2+iPadOS 3.2+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func CTFramesetterCreateFrame(
    _ framesetter: CTFramesetter,
    _ stringRange: CFRange,
    _ path: CGPath,
    _ frameAttributes: CFDictionary?
) -> CTFrame
```

## Parameters 

`framesetter`  

The framesetter used to create the frame.

`stringRange`  

The range, of the attributed string that was used to create the framesetter, that is to be typeset in lines fitted into the frame. If the length portion of the range is set to `0`, then the framesetter continues to add lines until it runs out of text or space.

`path`  

A CGPath object that specifies the shape of the frame. The path may be non-rectangular in versions of macOS 10.7 or later and versions of iOS 4.2 or later.

`frameAttributes`  

Additional attributes that control the frame filling process can be specified here, or `NULL` if there are no such attributes.

## Return Value

A reference to a new CTFrame object if the call was successful; otherwise, `NULL`.

## Discussion

This call creates a frame full of glyphs in the shape of the path provided by the `path` parameter. The framesetter continues to fill the frame until it either runs out of text or it finds that text no longer fits.

### Special Considerations

In versions of macOS prior to 10.7 and versions of iOS prior to 4.2, this function returns `NULL` if the CGPath specified by the `path` parameter is not rectangular.

## See Also

### Creating Frames

func CTFramesetterGetTypesetter(CTFramesetter) -> CTTypesetter

Returns the typesetter object being used by the framesetter.

