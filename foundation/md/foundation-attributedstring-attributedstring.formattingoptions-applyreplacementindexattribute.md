

- Foundation
- AttributedString
- AttributedString.FormattingOptions
-  applyReplacementIndexAttribute 

Type Property

# applyReplacementIndexAttribute

An option to add an attribute that marks replacements in localized strings.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
static let applyReplacementIndexAttribute: AttributedString.FormattingOptions
```

## Discussion

When you use this option, string formatting applies the replacementIndex key to the final range of each replacement. Its value is an `Int`, wrapping the integer ordinal of that particular replacement, such as the `2` in `%2$@`. This allows the developer to relate ranges to replacements even if a localizer modifies the word order.

