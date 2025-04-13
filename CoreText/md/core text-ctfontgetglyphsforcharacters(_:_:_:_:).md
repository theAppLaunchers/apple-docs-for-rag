

- Core Text
-  CTFontGetGlyphsForCharacters(\_:\_:\_:\_:) 

Function

# CTFontGetGlyphsForCharacters(\_:\_:\_:\_:)

Performs basic character-to-glyph mapping.

iOS 3.2+iPadOS 3.2+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func CTFontGetGlyphsForCharacters(
    _ font: CTFont,
    _ characters: UnsafePointer,
    _ glyphs: UnsafeMutablePointer,
    _ count: CFIndex
) -> Bool
```

## Parameters 

`font`  

The font reference.

`characters`  

An array of Unicode characters.

`glyphs`  

On output, points to an array of glyph values.

`count`  

The capacity of the character and glyph arrays.

## Return Value

`True` if the font could encode all Unicode characters; otherwise `False`.

## Discussion

Provides basic Unicode encoding for the given font, returning by reference an array of CGGlyph values corresponding to a given array of Unicode characters for the given font.

If a glyph could not be encoded, a value of `0` is passed back at the corresponding index in the `glyphs` array and the function returns `False`. It is the responsibility of the caller to handle the Unicode properties of the input characters.

## See Also

### Working with Glyphs

func CTFontDrawGlyphs(CTFont, UnsafePointer&lt;CGGlyph>, UnsafePointer&lt;CGPoint>, Int, CGContext)

Renders the given glyphs of a font at the specified positions in the supplied graphics context.

func CTFontGetLigatureCaretPositions(CTFont, CGGlyph, UnsafeMutablePointer&lt;CGFloat>?, CFIndex) -> CFIndex

Returns caret positions within a glyph.

