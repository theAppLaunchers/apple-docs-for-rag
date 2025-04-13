

- UIKit
- NSLayoutManager
-  allowsNonContiguousLayout 

Instance Property

# allowsNonContiguousLayout

A Boolean value that indicates whether the layout manager allows noncontiguous layout.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
var allowsNonContiguousLayout: Bool { get set }
```

## Discussion

For more information about noncontiguous layout, see Noncontiguous Layout.

## See Also

### Configuring the global layout manager options

var hasNonContiguousLayout: Bool

A Boolean value that indicates whether the layout manager currently has any areas of noncontiguous layout.

var showsInvisibleCharacters: Bool

A Boolean value that indicates whether to substitute visible glyphs for whitespace and other typically invisible characters.

var showsControlCharacters: Bool

A Boolean value that indicates whether the layout manager substitutes visible glyphs for control characters in the layout.

var usesFontLeading: Bool

A Boolean value that indicates whether the layout manager uses the leading of the font.

var backgroundLayoutEnabled: Bool { get set }

A Boolean value that indicates whether the layout manager generates glyphs and lays them out when the app’s run loop is idle.

var limitsLayoutForSuspiciousContents: Bool

A Boolean value that indicates whether the layout manager avoids laying out unusually long or suspicious input.

var usesDefaultHyphenation: Bool

A Boolean value that indicates whether the layout manager uses the default hyphenation rules to wrap lines.

