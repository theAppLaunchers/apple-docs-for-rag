

- Core Text
-  CTFramesetterCreateWithTypesetter(\_:) 

Function

# CTFramesetterCreateWithTypesetter(\_:)

Creates a framesetter directly from a typesetter.

iOS 12.0+iPadOS 12.0+Mac Catalyst 13.1+macOS 10.14+tvOS 12.0+visionOS 1.0+watchOS 5.0+

``` source
func CTFramesetterCreateWithTypesetter(_ typesetter: CTTypesetter) -> CTFramesetter
```

## Parameters 

`typesetter`  

The typesetter that the framesetter uses to lay out text.

## Return Value

This function returns a reference to a `CTFramesetter` object.

## Discussion

Each framesetter uses a typesetter internally to perform line breaking and other contextual analysis according to the characters in a string. This function allows the framesetter to use a typesetter that the system constructs using specific options.

## See Also

### Creating a Framesetter

func CTFramesetterCreateWithAttributedString(CFAttributedString) -> CTFramesetter

Creates an immutable framesetter object from an attributed string.

