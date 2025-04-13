

- Swift
- Character
-  isCurrencySymbol 

Instance Property

# isCurrencySymbol

A Boolean value indicating whether this character represents a currency symbol.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var isCurrencySymbol: Bool { get }
```

## Discussion

For example, the following characters all represent currency symbols:

- “\$” (U+0024 DOLLAR SIGN)

- “¥” (U+00A5 YEN SIGN)

- “€” (U+20AC EURO SIGN)

## See Also

### Inspecting a Character

var isLetter: Bool

A Boolean value indicating whether this character is a letter.

var isPunctuation: Bool

A Boolean value indicating whether this character represents punctuation.

var isNewline: Bool

A Boolean value indicating whether this character represents a newline.

var isWhitespace: Bool

A Boolean value indicating whether this character represents whitespace, including newlines.

var isSymbol: Bool

A Boolean value indicating whether this character represents a symbol.

var isMathSymbol: Bool

A Boolean value indicating whether this character represents a symbol that naturally appears in mathematical contexts.

