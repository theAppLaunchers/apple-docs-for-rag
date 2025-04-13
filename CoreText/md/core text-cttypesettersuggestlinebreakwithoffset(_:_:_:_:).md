

- Core Text
-  CTTypesetterSuggestLineBreakWithOffset(\_:\_:\_:\_:) 

Function

# CTTypesetterSuggestLineBreakWithOffset(\_:\_:\_:\_:)

Suggests a contextual line breakpoint based on the width provided and the specified offset.

iOS 3.2+iPadOS 3.2+Mac Catalyst 13.1+macOS 10.6+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func CTTypesetterSuggestLineBreakWithOffset(
    _ typesetter: CTTypesetter,
    _ startIndex: CFIndex,
    _ width: Double,
    _ offset: Double
) -> CFIndex
```

## Parameters 

`typesetter`  

The typesetter that creates the line. This parameter is required and cannot be set to `NULL`.

`startIndex`  

The starting point for the line-break calculations. The break calculations include the character starting at `startIndex`.

`width`  

The requested line-break width.

`offset`  

The line position offset.

## Return Value

A count of the characters from `startIndex` and `offset` that would cause the line break. The value returned can be used to construct a character range for CTTypesetterCreateLine(_:_:).

## Discussion

The line break can be triggered either by a hard-break character in the stream or by filling the specified width with characters.

## See Also

### Breaking Lines

func CTTypesetterSuggestLineBreak(CTTypesetter, CFIndex, Double) -> CFIndex

Suggests a contextual line breakpoint based on the width provided.

func CTTypesetterSuggestClusterBreak(CTTypesetter, CFIndex, Double) -> CFIndex

Suggests a cluster line breakpoint based on the width provided.

func CTTypesetterSuggestClusterBreakWithOffset(CTTypesetter, CFIndex, Double, Double) -> CFIndex

Suggests a cluster line breakpoint based on the specified width and line offset.

