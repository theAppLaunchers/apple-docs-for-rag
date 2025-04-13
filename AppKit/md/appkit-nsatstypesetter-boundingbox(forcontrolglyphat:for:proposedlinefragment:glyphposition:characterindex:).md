

- AppKit
- NSATSTypesetter
-  boundingBox(forControlGlyphAt:for:proposedLineFragment:glyphPosition:characterIndex:) 

Instance Method

# boundingBox(forControlGlyphAt:for:proposedLineFragment:glyphPosition:characterIndex:)

Returns the bounding rectangle for a control glyph, at the specified glyph position and character index in the text container.

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

## Discussion

Returns the bounding rectangle for the control glyph at `glyphIndex`, at the given `glyphPosition` and character index `charIndex`, in `textContainer`. The proposed line fragment rectangle is specified by `proposedRect`.

The typesetter calls this method when it encounters an NSControlGlyph. The default behavior is to return zero width for control glyphs. A subclass can override this method to do something different, such as implement a way to display control characters.

NSGlyphGenerator can choose whether or not to map control characters to NSControlGlyph. Tab characters, for example, do not use this facility.

## See Also

### Laying Out Glyphs

func getLineFragmentRect(UnsafeMutablePointer&lt;NSRect>, usedRect: UnsafeMutablePointer&lt;NSRect>, forParagraphSeparatorGlyphRange: NSRange, atProposedOrigin: NSPoint)

Calculates the line fragment rectangle and the portion of the rectangle that contains marks.

func hyphenCharacter(forGlyphAt: Int) -> UTF32Char

Returns the hyphen character to be inserted after the specified glyph when hyphenation is enabled in the layout manager.

func hyphenationFactor(forGlyphAt: Int) -> Float

Returns the hyphenation factor in effect at the specified glyph index.

func shouldBreakLine(byHyphenatingBeforeCharacterAt: Int) -> Bool

Breaks a line by hyphenating before the character at the specified index.

func shouldBreakLine(byWordBeforeCharacterAt: Int) -> Bool

Breaks a line by word-wrapping before the character at the specified index.

func willSetLineFragmentRect(UnsafeMutablePointer&lt;NSRect>, forGlyphRange: NSRange, usedRect: UnsafeMutablePointer&lt;NSRect>, baselineOffset: UnsafeMutablePointer&lt;CGFloat>)

Notifies subclasses that the typesetter is about to set a new line fragment.

func setHardInvalidation(Bool, forGlyphRange: NSRange)

Sets a Boolean value that determines whether the layout manager invalidates the specified portion of the glyph cache.

