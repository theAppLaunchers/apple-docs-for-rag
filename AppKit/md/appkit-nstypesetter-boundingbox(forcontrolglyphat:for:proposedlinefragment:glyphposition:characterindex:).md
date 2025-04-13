

- AppKit
- NSTypesetter
-  boundingBox(forControlGlyphAt:for:proposedLineFragment:glyphPosition:characterIndex:) 

Instance Method

# boundingBox(forControlGlyphAt:for:proposedLineFragment:glyphPosition:characterIndex:)

Returns the bounding rectangle for the specified control glyph with the specified parameters.

macOS

``` source
func boundingBox(
    forControlGlyphAt glyphIndex: Int,
    for textContainer: NSTextContainer,
    proposedLineFragment proposedRect: NSRect,
    glyphPosition: NSPoint,
    characterIndex charIndex: Int
) -> NSRect
```

## Parameters 

`glyphIndex`  

The index of the control glyph in question.

`textContainer`  

The text container to use to calculate the position.

`proposedRect`  

The proposed line fragment rectangle.

`glyphPosition`  

The position of the glyph in `textContainer`.

`charIndex`  

The character index in `textContainer`.

## Return Value

The bounding rectangle of the control glyph at `glyphIndex`, at the given `glyphPosition` and character index `charIndex`, in `textContainer`.

## Discussion

The typesetter calls this method when it encounters a control glyph. The default behavior is to return zero width for control glyphs. A subclass can override this method to do something different, such as implement a way to display control characters.

NSGlyphGenerator can choose whether or not to map control characters to NSControlGlyph. Tab characters, for example, do not use this facility.

## See Also

### Laying out glyphs

func layoutGlyphs(in: NSLayoutManager, startingAtGlyphIndex: Int, maxNumberOfLineFragments: Int, nextGlyphIndex: UnsafeMutablePointer&lt;Int>)

Lays out glyphs in the specified layout manager starting at a specified glyph.

Deprecated

func getLineFragmentRect(NSRectPointer, usedRect: NSRectPointer, forParagraphSeparatorGlyphRange: NSRange, atProposedOrigin: NSPoint)

Calculates the line fragment rectangle and line fragment used rectangle for blank lines.

func getLineFragmentRect(NSRectPointer!, usedRect: NSRectPointer!, remaining: NSRectPointer!, forStartingGlyphAt: Int, proposedRect: NSRect, lineSpacing: CGFloat, paragraphSpacingBefore: CGFloat, paragraphSpacingAfter: CGFloat)

Calculates line fragment rectangle, line fragment used rectangle, and remaining rectangle for a line fragment.

func hyphenCharacter(forGlyphAt: Int) -> UTF32Char

Returns the hyphen character to be inserted after the specified glyph.

func hyphenationFactor(forGlyphAt: Int) -> Float

Returns the hyphenation factor in effect at a specified location.

func shouldBreakLine(byHyphenatingBeforeCharacterAt: Int) -> Bool

Returns whether the line being laid out should be broken by hyphenating at the specified character.

func shouldBreakLine(byWordBeforeCharacterAt: Int) -> Bool

Returns whether the line being laid out should be broken by a word break at the specified character.

func willSetLineFragmentRect(NSRectPointer, forGlyphRange: NSRange, usedRect: NSRectPointer, baselineOffset: UnsafeMutablePointer&lt;CGFloat>)

Called by the typesetter just prior to storing the actual line fragment rectangle location in the layout manager.

func setHardInvalidation(Bool, forGlyphRange: NSRange)

Sets whether to force the layout manager to invalidate the specified portion of the glyph cache when invalidating layout.

