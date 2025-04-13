

- AppKit
- NSFont
-  userFixedPitchFont(ofSize:) 

Type Method

# userFixedPitchFont(ofSize:)

Returns the font used by default for documents and other text under the user’s control (that is, text whose font the user can normally change), when that font should be fixed-pitch, in the specified size.

macOS

``` source
class func userFixedPitchFont(ofSize fontSize: CGFloat) -> NSFont?
```

## Parameters 

`fontSize`  

The size in points to which the font is scaled.

## Return Value

A font object of the specified size.

## Discussion

If `fontSize` is 0 or negative, returns the fixed-pitch font at the default size.

The system does not guarantee that all the glyphs in a fixed-pitch font are the same width. For example, certain Japanese fonts are dual-pitch, and other fonts may have nonspacing marks that can affect the display of other glyphs.

## See Also

### Related Documentation

init?(name: String, size: CGFloat)

Creates a font object for the specified font name and font size.

class func setUserFixedPitch(NSFont?)

Sets the font used by default for documents and other text under the user’s control, when that font should be fixed-pitch, to the specified font.

### Creating User Fonts

class func userFont(ofSize: CGFloat) -> NSFont?

Returns the font used by default for documents and other text under the user’s control (that is, text whose font the user can normally change), in the specified size.

