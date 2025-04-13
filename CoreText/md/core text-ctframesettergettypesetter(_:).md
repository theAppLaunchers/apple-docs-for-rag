

- Core Text
-  CTFramesetterGetTypesetter(\_:) 

Function

# CTFramesetterGetTypesetter(\_:)

Returns the typesetter object being used by the framesetter.

iOS 3.2+iPadOS 3.2+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func CTFramesetterGetTypesetter(_ framesetter: CTFramesetter) -> CTTypesetter
```

## Parameters 

`framesetter`  

The framesetter from which a typesetter is requested.

## Return Value

A reference to a CTTypesetter object if the call was successful; otherwise, `NULL`. The framesetter maintains a reference to the returned object, which should not be released by the caller.

## Discussion

Each framesetter uses a typesetter internally to perform line breaking and other contextual analysis based on the characters in a string; this function returns the typesetter being used by a particular framesetter in case the caller would like to perform other operations on that typesetter.

## See Also

### Creating Frames

func CTFramesetterCreateFrame(CTFramesetter, CFRange, CGPath, CFDictionary?) -> CTFrame

Creates an immutable frame using a framesetter.

