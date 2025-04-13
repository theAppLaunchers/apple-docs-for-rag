

- AppKit
- NSFont
-  coveredCharacterSet 

Instance Property

# coveredCharacterSet

The character set containing all of the nominal characters that the font can render.

macOS

``` source
var coveredCharacterSet: CharacterSet { get }
```

## Discussion

The nominal character set is all of the entries in the font’s `cmap` table.

The number of glyphs supported by a given font is often larger than the number of characters contained in the character set returned by this method. This is because characters and glyphs have a many-to-many mapping, rather than a strict one-to-one correspondence. In some cases a character may be represented by multiple glyphs, such as an “é” which may be an “e” glyph combined with an acute accent glyph “´”. In other cases, a single glyph may represent multiple characters, as in the case of a ligature, or joined letter. See Typographical Concepts in Cocoa Text Architecture Guide for more information.

## See Also

### Getting Font Metrics and Information

var pointSize: CGFloat

The point size of the font.

var fontDescriptor: NSFontDescriptor

The font descriptor object for the font.

var isFixedPitch: Bool

A Boolean value indicating whether all glyphs in the font have the same advancement.

var mostCompatibleStringEncoding: UInt

The string encoding that works best with the font.

Advanced Font Metrics

Retrieve details about ascender and descender heights, glyph bounding rectangles, glyph advancements, and more.

