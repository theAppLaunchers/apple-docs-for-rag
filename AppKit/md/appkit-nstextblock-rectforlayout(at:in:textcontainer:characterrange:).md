

- AppKit
- NSTextBlock
-  rectForLayout(at:in:textContainer:characterRange:) 

Instance Method

# rectForLayout(at:in:textContainer:characterRange:)

Returns the rectangle within which glyphs should be laid out for the specified arguments.

macOS

``` source
func rectForLayout(
    at startingPoint: NSPoint,
    in rect: NSRect,
    textContainer: NSTextContainer,
    characterRange charRange: NSRange
) -> NSRect
```

## Parameters 

`startingPoint`  

The location, in container coordinates, where layout begins.

`rect`  

The rectangle in which the block is constrained to lie. For top-level blocks, this is the container rectangle of `textContainer`; for nested blocks, this is the layout rectangle of the enclosing block.

`textContainer`  

The text container being used for the layout.

`charRange`  

The range of the characters in the NSTextStorage object whose glyphs are to be drawn.

## Return Value

The rectangle within which glyphs should be laid out.

## Discussion

This method is called by the typesetter before the text block is laid out to return the rectangle within which glyphs should be laid out.

## See Also

### Determining size and position of a text block

func boundsRect(forContentRect: NSRect, in: NSRect, textContainer: NSTextContainer, characterRange: NSRange) -> NSRect

Returns the rectangle the text in the block actually occupies, including padding, borders, and margins.

